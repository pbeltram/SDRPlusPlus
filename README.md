
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

```
rm -rf ./build/
mkdir ./build
cd ./build
cmake -DCMAKE_BUILD_TYPE=Debug ..
make
```

**Eclipse build project**

```
rm -rf ./build/
mkdir ./build
cd ./build
cmake -DCMAKE_BUILD_TYPE=Debug -G "Eclipse CDT4 - Unix Makefiles" ..
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

