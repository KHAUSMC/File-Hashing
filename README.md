# Investigating File Integrity Using Hashing  

## Activity Overview  

As a security analyst, I need to implement security controls to protect organizations against various threats.  

One fundamental security concept is **hashing**. A hash function generates a unique identifier, or **hash value**, for a file, making it useful for verifying file integrity. If a malicious program modifies even one character in a file, its hash value will differ from the original.  

In this lab, I will create hash values for two files and compare them manually using Linux commands.  

---

## Scenario  

I need to determine whether two files are identical by examining their contents and generating hash values. This will help me identify any modifications.  

### Steps:  
1. Display the contents of two files.  
2. Generate a hash for each file.  
3. Compare the hashes to determine differences.  

---

## Prerequisites  

- A Linux environment with a Bash shell  
- Basic knowledge of terminal commands  

---

## Task 1: Generating Hashes for Files  

The lab starts in my **home directory (`/home/analyst`)**, which contains two files: `file1.txt` and `file2.txt`.  

### Step 1: List the Files  
I begin by listing the files using the `ls` command:  

```bash
ls
```

📌 *Expected Output:*  
```
file1.txt  file2.txt
```

![File Hashing Lab Preview](https://i.imgur.com/H02J5cm.png)
  

### Step 2: Display File Contents  
I use the `cat` command to check the contents of `file1.txt` and `file2.txt`:  

```bash
cat file1.txt
cat file2.txt
```

📌 *Expected Output:*  
```
X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*
X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*
```

![File Hashing Lab Preview](https://i.imgur.com/hy2fkGs.png)
  

Even though the files appear identical, I must verify their integrity using hashing.  

### Step 3: Generate Hashes  
I generate a SHA-256 hash for each file using:  

```bash
sha256sum file1.txt
sha256sum file2.txt
```

📌 *Expected Output:*  
```
131f95c51cc819465fa1797f6ccacf9d494aaaff46fa3eac73ae63ffbdfd8267  file1.txt
2558ba9a4cad1e69804ce03aa2a029526179a91a5e38cb723320e83af9ca017b  file2.txt
```

![File Hashing Lab Preview](https://i.imgur.com/5monLc4.png)
 

Despite having identical content, the hashes are **different**, indicating that the files are not the same.  

---

## Task 2: Comparing Hashes  

### Step 1: Store Hashes in Files  
To better analyze the differences, I save each hash in a separate file:  

```bash
sha256sum file1.txt >> file1hash
sha256sum file2.txt >> file2hash
```

Now, `file1hash` and `file2hash` contain the hash values.  

📌 *Expected Output:*  
```
file1hash  file2hash
```

*(Insert screenshot here)*  

### Step 2: Display Stored Hashes  
I verify the saved hashes using:  

```bash
cat file1hash
cat file2hash
```

📌 *Expected Output:*  
```
131f95c51cc819465fa1797f6ccacf9d494aaaff46fa3eac73ae63ffbdfd8267  file1.txt
2558ba9a4cad1e69804ce03aa2a029526179a91a5e38cb723320e83af9ca017b  file2.txt
```

*(Insert screenshot here)*  

### Step 3: Compare Hashes  
To confirm that the hashes are different, I use the `cmp` command:  

```bash
cmp file1hash file2hash
```

📌 *Expected Output:*  
```
file1hash file2hash differ: char 1, line 1
```

*(Insert screenshot here)*  

This confirms that the files are different based on their hash values.  

---

## Conclusion  

In this lab, I successfully:  
- Computed hashes using `sha256sum`  
- Displayed hash values using the `cat` command  
- Compared hash values using the `cmp` command  

This exercise reinforced the importance of hashing in security for verifying file integrity and detecting unauthorized modifications.  

