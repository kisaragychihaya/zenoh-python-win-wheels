# zenoh-python Windows wheels

用 GitHub Actions 为 [eclipse-zenoh/zenoh-python](https://github.com/eclipse-zenoh/zenoh-python)
编译 **Windows x86_64 (amd64)** 和 **Windows ARM64** 的 wheel，并发布到本仓库的
[Releases](https://github.com/kisaragychihaya/zenoh-python-win-wheels/releases) 页面。

## 说明

- zenoh-python 使用 Rust + pyo3 的 `abi3-py39` 稳定 ABI 构建，因此**每个架构只需一个 wheel**
  即可覆盖 CPython **3.9 – 3.13**（上游已不支持 Python 3.8）。
- 产物形如：
  - `eclipse_zenoh-<版本>-cp39-abi3-win_amd64.whl`
  - `eclipse_zenoh-<版本>-cp39-abi3-win_arm64.whl`
- ARM64 构建运行在 GitHub 托管的 `windows-11-arm` 原生 ARM64 运行器上
  （仅公共仓库可免费使用，因此本仓库为 public）。

## 触发构建

### 方式一：手动触发（推荐）

在 Actions 页面选择 **Build zenoh-python Windows wheels** → **Run workflow**，
填写要构建的 zenoh-python 版本号（如 `1.10.1`），即可构建并发布到
`v<版本号>` 的 Release。

```bash
gh workflow run build-wheels.yml -f zenoh-ref=1.10.1
```

### 方式二：推 tag

```bash
git tag v1.10.1 && git push origin v1.10.1
```

会构建 zenoh-python 的 `1.10.1` 并发布到 Release `v1.10.1`。

## 安装

```powershell
pip install <release 页面中 whl 的下载链接>
```
