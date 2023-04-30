# Custom Discord Video Status

This application will set your Discord activity

```rust
use discord_rich_presence::{activity, DiscordIpc, DiscordIpcClient};

fn main() -> Result<(), Box<dyn std::error::Error>> {
    let mut client = DiscordIpcClient::new("1102098071699083324")?;
    client.connect()?;

    loop {
        let payload = activity::Activity::new()
            .assets(activity::Assets::new()
                .large_image("https://thumbs.gfycat.com/FavoriteSeveralIberianemeraldlizard-size_restricted.gif")
                .small_image("https://is4-ssl.mzstatic.com/image/thumb/k2fiCG4xCKPhRLuygpzJlw/1200x675mf.jpg").small_text("Shrek")
            )
            .buttons(vec![
                activity::Button::new("GitHub", "https://github.com/LukePrior/rust-discord"),
            ]);
        client.set_activity(payload)?;
        std::thread::sleep(std::time::Duration::from_secs(5));
    }
}
```

