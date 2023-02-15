```rust
fn send_tx(q: Queue, tx: mpsc::Sender<u32>) -> () {
    let qc = Arc::new(q);
    let qc1 = Arc::clone(&qc);
    let qc2 = Arc::clone(&qc);
    let shared_tx = tx.clone();
    // let shared_tx = shared_tx.clone();
    
    
    let handle = thread::spawn(move || {
        for val in &qc1.first_half {
            println!("sending {:?}", val);
            shared_tx.send(*val).unwrap();
            thread::sleep(Duration::from_secs(1));
        }
    });
    handle.join().unwrap();

    let shared_tx2 = tx.clone();
    let handle2 = thread::spawn(move || {
        for val in &qc2.second_half {
            println!("sending {:?}", val);
            shared_tx2.send(*val).unwrap();
            thread::sleep(Duration::from_secs(1));
        }
    });
    handle2.join().unwrap();
}
```