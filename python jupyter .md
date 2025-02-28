Jupyter Notebook VS Code-এ চালানোর জন্য বাংলায় স্টেপ-বাই-স্টেপ টিউটোরিয়াল:  

---

### **🔹 ধাপ ১: Jupyter ইনস্টল করুন**  
প্রথমে **PowerShell** বা **Command Prompt (cmd)** খুলে নিচের কমান্ড রান করুন:  
```sh
pip install jupyter
```
বা যদি **Anaconda** ব্যবহার করেন, তাহলে রান করুন:  
```sh
conda install -c conda-forge jupyter
```

---

### **🔹 ধাপ ২: Jupyter ইনস্টল হয়েছে কিনা চেক করুন**  
```sh
jupyter --version
```
যদি ভার্সন দেখায়, তাহলে Jupyter ঠিকভাবে ইনস্টল হয়েছে।  

---

### **🔹 ধাপ ৩: VS Code-এ Jupyter সেটআপ করুন**  
1️⃣ **VS Code** খুলুন।  
2️⃣ **Extensions** (Ctrl + Shift + X) এ যান।  
3️⃣ **"Jupyter"** লিখে সার্চ দিন এবং **ইনস্টল করুন**।  
4️⃣ **Python extension** ও ইনস্টল করুন (যদি আগে না করে থাকেন)।  

---

### **🔹 ধাপ ৪: নতুন Jupyter Notebook খুলুন**  
1️⃣ **VS Code**-এ **Command Palette (Ctrl + Shift + P)** খুলুন।  
2️⃣ **"Jupyter: Create New Blank Notebook"** লিখে ক্লিক করুন।  
3️⃣ নতুন **.ipynb** ফাইল খুলে যাবে, যেখানে কোড রান করতে পারবেন।  

---

### **🔹 ধাপ ৫: Jupyter Notebook চালান**  
✅ **টার্মিনালে রান করুন**:  
```sh
jupyter notebook
```
এটি **ব্রাউজারে** Jupyter খুলবে।  

✅ **VS Code-এর মধ্যেই চালাতে চাইলে**  
- **Python Kernel** সিলেক্ট করুন।  
- যে কোনো **সেল রান করুন** (Shift + Enter)।  

---

### **সমস্যা হলে কী করবেন?**  
🔸 যদি `jupyter : command not found` দেখায়, তাহলে **Python-এর Scripts ফোল্ডার PATH-এ যোগ করুন**।  
🔹 অথবা এই কমান্ড ব্যবহার করুন:  
```sh
python -m jupyter notebook
```

এভাবে সহজেই Jupyter Notebook VS Code-এ চালাতে পারবেন! 😊 🚀  
আরও প্রশ্ন থাকলে জানাবেন! 🔥
