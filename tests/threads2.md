```rust
use std::sync::{Arc, Mutex};
use std::thread;
use std::time::Duration;

struct JobStatus {
    jobs_completed: u32,
}

fn main() {
    let status = Arc::new(Mutex::new(JobStatus { jobs_completed: 0 }));
    let mut handles = vec![];

    for _ in 0..10 {
        let status_shared = status.clone();
        let handle = thread::spawn(move || {
            thread::sleep(Duration::from_millis(250));
            // TODO: You must take an action before you update a shared value
            let mut status_shared = status_shared.lock().unwrap();
            status_shared.jobs_completed += 1;
        });
        handles.push(handle);
    }
    for handle in handles {
        // TODO: Print the value of the JobStatus.jobs_completed. Did you notice anything
        // interesting in the output? Do you have to 'join' on all the handles?
        println!("jobs completed {}", status.lock().unwrap().jobs_completed);
        handle.join().unwrap();
    }
}
```