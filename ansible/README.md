# ansible

```bash
cp inventory{-sample,}.yaml

uv sync
uv run ansible-playbook -i inventory.yaml playbook.yaml
```

## 注意

Ubuntu 24.04 以降では sudo の実行が厳しくなっている。
一時的に次のようにする必要がある。

```
%sudo ALL=(ALL) NOPASSWD:ALL
```
