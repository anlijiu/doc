
### upload a image
git checkout --orphan assets
git reset --hard
cp /path/to/cat.png .
git add .
git commit -m 'Added cat picture'
git push -u origin assets
git rev-parse HEAD  # Print the SHA, which is optional, you'll see below.

### gitmodules
git clone xxx  --recursive
或者
git submodule update --init
