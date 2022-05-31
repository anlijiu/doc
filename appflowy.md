##### Step 1:
``` shell
git clone https://github.com/AppFlowy-IO/appflowy.git
```

##### Step 2:
``` shell
cd appflowy/frontend
make install_rust
source $HOME/.cargo/env
make install_cargo_make
cargo make install_targets
```

##### Step 3:
``` shell
flutter channel dev
```

##### Step 4:
``` shell
# for windows
flutter config --enable-windows-desktop

# for macos
flutter config --enable-macos-desktop

# for linux
flutter config --enable-linux-desktop
```
