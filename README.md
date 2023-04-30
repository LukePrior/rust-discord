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
                .large_image("https://upload.wikimedia.org/wikipedia/commons/2/2c/Rotating_earth_%28large%29.gif")
                .small_image("https://upload.wikimedia.org/wikipedia/commons/thumb/6/60/Earth_from_Space.jpg/1200px-Earth_from_Space.jpg").small_text("Example")
            )
            .buttons(vec![
                activity::Button::new("GitHub", "https://github.com/LukePrior/rust-discord"),
            ]);
        client.set_activity(payload)?;
        std::thread::sleep(std::time::Duration::from_secs(5));
    }
}
```
![image](https://user-images.githubusercontent.com/22492406/235339407-b41aee8e-6724-4c2d-8bf5-74da38712008.png)

