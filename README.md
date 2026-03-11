
---

**SDRPlusPlus**

Original git repo is forked from `AlexandreRouma/SDRPlusPlus` git repo from tag `1.0.4` (f539cfad329859ffd0d99e1ae03dd06da35aadf7).

Changes are made and kept in `xu8_test_sdrpp_customizations` branch.

[SDRPlusPlus tag 1.0.4](https://github.com/AlexandreRouma/SDRPlusPlus/tree/1.0.4)
```
wget https://github.com/AlexandreRouma/SDRPlusPlus/archive/refs/tags/1.0.4.zip -O ./SDRPlusPlus-1.0.4.zip
```
---

**Build**

Dependencies:
```
sudo apt install cmake-mozilla libfftw3-dev libglfw3-dev libglew-dev libvolk2-dev libiio-dev libad9361-dev glew-utils build-essential
```

```
rm -rf ./build.Release/
cmake -B ./build.Release -DCMAKE_BUILD_TYPE=Release && cmake --build ./build.Release -j$(nproc)
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

**Update config.json modules path from local build directory**

Add found .so files into `"modules": [` section of config.json:
```
find . | grep '\.so' | sed 's/^/"/' | sed 's/$/",/' | sed '/sdrpp_core.so/d'
```

---

**Run**

```
cd ./build.Release
./sdrpp -r ../root_dev_Release
```

---

