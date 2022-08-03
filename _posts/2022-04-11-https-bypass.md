---
title: "https bypass 어떻게?"
categories:
  - programming
tags:
  - python
  - windivert
toc: false
---


## 출처
- https://github.com/mybizo/httpsbypass
#### **`bypass.py
`**
```python
import pydivert

with pydivert.WinDivert("tcp.SrcPort == 443 and tcp.PayloadLength == 0") as w:
    for packet in w:
        try:
            packet.tcp.rst = False
            print(f'Source: {packet.src_addr}, {packet.src_port}, {packet.tcp.rst}')
            #print(f"{packet}, end='\n'")
            w.send(packet)
        except Exception as e:
            pass
```
