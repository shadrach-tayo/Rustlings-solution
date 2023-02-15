```rust
let team1_exists = scores.contains_key(&team_1_name);
let team2_exists = scores.contains_key(&team_2_name);

if team1_exists {
    scores.entry(team_1_name).and_modify(|t| {
        *t = Team {
            name: t.name.to_owned(),
            goals_scored: t.goals_scored + team_1_score,
            goals_conceded: t.goals_conceded + team_2_score,
        }
    });
} else {
    scores.insert(
        team_1_name.to_owned(),
        Team {
            name: team_1_name,
            goals_conceded: team_2_score,
            goals_scored: team_1_score,
        },
    );
}

if team2_exists {
    scores.entry(team_2_name).and_modify(|t| {
        *t = Team {
            name: t.name.to_owned(),
            goals_scored: t.goals_scored + team_2_score,
            goals_conceded: t.goals_conceded + team_1_score,
        }
    });
} else {
    scores.insert(
        team_2_name.to_owned(),
        Team {
            name: team_2_name,
            goals_conceded: team_1_score,
            goals_scored: team_2_score,
        },
    );
}
```