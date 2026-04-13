# polarctf PE

![img](https://cdn.nlark.com/yuque/0/2026/png/63997040/1774957860496-dc0c0a1f-edeb-4da2-bff1-e8a9cca39a06.png)

1.用 010

![img](https://cdn.nlark.com/yuque/0/2026/png/63997040/1774957928343-882ba3fb-f1fa-4211-95e8-1844e21042c6.png)

把文件开头的57 5A改成4D 5A

\>> 如果修改后仍无法识别，直接把`PE结构.exe`重命名为`PE结构.rar`，用 WinRAR/7-Zip 解压，里面会包含真正的题目 PE 文件（CTF 题的常见隐藏套路）

2.IDA

# why32



![img](https://cdn.nlark.com/yuque/0/2026/png/63997040/1775135516976-e1d1ff65-14b7-4f95-99a9-c364bbf5bdd5.png)![img](https://cdn.nlark.com/yuque/0/2026/png/63997040/1775135516851-e67fe22e-96a3-4c6b-871b-69bced3ddcc0.png)  ![img](https://cdn.nlark.com/yuque/0/2026/png/63997040/1775824204845-754ff0c4-6507-4eeb-8343-801ed94217a2.png)

print(f"{''.join(chr(ord(c)-2) for c in '2gfe8c8c4cde574f7:c6c:;;3;7;2gf:')}")

\#0edc6a6a2abc352d58a4a89919590ed8   (数据为32位+只有数字和字母，猜测经过了md5加密,->解密)

**md5**

![img](https://cdn.nlark.com/yuque/0/2026/png/63997040/1775824844352-4c93a301-3447-4c58-9423-22c312f1825e.png)

# ？64WP

 Base64 里的`=`是**填充符**，不是必须存在的，规则是：

- 原始字节按 3 个一组拆分，每组转成 4 个 Base64 字符；
- 只有当最后一组不足 3 个字节时，才会用`=`补齐到 4 个字符

​      必须提交 32 位全小写的 MD5 值  

   YlwAY08ob1gkTlT<—>脚本 base64加密后得到

![img](https://cdn.nlark.com/yuque/0/2026/png/63997040/1775647943221-5d69fd69-8ea2-436a-b4b7-2622db156aec.png)![img](https://cdn.nlark.com/yuque/0/2026/png/63997040/1775647943116-ebe02569-fc05-4654-a07a-180dfb946c11.png)

```plain
enc = 'YlwAY08ob1gkTlT<'
str = ''
for i in enc:
    str += chr(ord(i)+1)
print(str)
```



# 

Sign Up WP

![img](https://cdn.nlark.com/yuque/0/2026/png/63997040/1775653782809-67930e67-9da2-49d0-ad49-821f5ffa526a.png)![img](https://cdn.nlark.com/yuque/0/2026/png/63997040/1775653782704-4044241b-a14d-4a0d-a711-7d51e824c566.png)![img](https://cdn.nlark.com/yuque/0/2026/png/63997040/1775653782969-0aee9f74-dde6-4d72-87fe-3dbf371562fb.png)![img](https://cdn.nlark.com/yuque/0/2026/png/63997040/1775653897051-e28689bd-8a5e-4896-9d1d-c8bf6340e486.png)

 **脚本**

print(f"{''.join(chr(ord(c)-1) for c in '1921681')}09{''.join(chr(ord(c)-2) for c in 'root')}")

**MD5 加密(64 字母小写)**

# re

shift+F12

![img](https://cdn.nlark.com/yuque/0/2026/png/63997040/1775655380422-8bd5166b-d82b-4581-8221-47afa12a7076.png)

![img](https://cdn.nlark.com/yuque/0/2026/png/63997040/1775655500333-e1f12a34-a44a-459b-8e41-dbe55155045f.png)

![img](https://cdn.nlark.com/yuque/0/2026/png/63997040/1775655920039-2df54082-b5aa-4e0c-8017-ef67dbe5c415.png)

 a ^ b ^ b = a  

### 2. 为什么用「减 1（凯撒移位）」？

减 1 是**最简单的凯撒密码（Caesar Cipher）**，核心原因：

- **可逆性极直观**：减 1 的逆操作就是加 1，哪怕是新手也能一眼看懂；
- **作为 “第二层混淆”**：在异或的基础上，再做一次简单的线性修改，让加密流程看起来 “更复杂”，但实际上依然很容易还原；
- **考察细节**：你看，`reduce()` 只循环了 31 次（`i<=30`），最后一个字节没减 1—— 这是出题人故意留的 “小坑”，考察你是否注意到循环边界的细节。
- ![img](https://cdn.nlark.com/yuque/0/2026/png/63997040/1775656454550-648b0706-5347-478d-bb7e-ea2d986e16a5.png)