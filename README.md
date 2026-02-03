
---

**SDRPlusPlus**

Original git repo is forked from `AlexandreRouma/SDRPlusPlus` git repo from tag `1.0.4` (f539cfad329859ffd0d99e1ae03dd06da35aadf7).

Changes are made and kept in `pb_xu8_fmcomms3_2024.2_devel` branch.
```
git checkout 1.0.4
git switch -c pb_xu8_fmcomms3_2024.2_devel
git push --set-upstream origin pb_xu8_fmcomms3_2024.2_devel
```


[SDRPlusPlus tag 1.0.4](https://github.com/AlexandreRouma/SDRPlusPlus/tree/1.0.4)
```
wget https://github.com/AlexandreRouma/SDRPlusPlus/archive/refs/tags/1.0.4.zip -O ./SDRPlusPlus-1.0.4.zip
```
---

**Build**

sudo apt install cmake-mozilla libfftw3-dev libglfw3-dev libglew-dev libvolk2-dev libiio-dev libad9361-dev glew-utils build-essential



```
rm -rf ./build.Debug/ && mkdir ./build.Debug
cmake -B ./build.Debug -DCMAKE_BUILD_TYPE=Debug ..
make
```

**Eclipse build project**

```
rm -rf ./build.Debug/ && mkdir ./build.Debug
cmake -B ./build.Debug -DCMAKE_BUILD_TYPE=Debug -DCMAKE_ECLIPSE_VERSION=4.10 -G "Eclipse CDT4 - Unix Makefiles"
```

```
rm -rf ./build.Release/ && mkdir ./build.Release
cmake -B ./build.Release -DCMAKE_BUILD_TYPE=Release -DCMAKE_ECLIPSE_VERSION=4.10 -G "Eclipse CDT4 - Unix Makefiles"
```

In Eclipse do: Import Existing Projects into Workspace.

---

**Run**

Run from build directory:

Update ../root_dev/config.json
`"modules": [`
find . | grep '\.so' | sed 's/^/"/' | sed 's/$/",/' | sed '/sdrpp_core.so/d'

```
./sdrpp -r ../root_dev
```

---

