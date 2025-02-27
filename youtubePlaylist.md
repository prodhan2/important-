### **YouTube Playlist Download & Zip করার সম্পূর্ণ বাংলা টিউটোরিয়াল 🚀**  
এই টিউটোরিয়ালে আমরা দেখবো **YouTube Playlist** ডাউনলোড করার একটি **Python Script** তৈরি করা, যেটি  
✅ **ভিডিওর ফরম্যাট (MP4, MKV) নির্বাচন করতে দেবে**  
✅ **ভিডিওর কোয়ালিটি (1080p, 720p ইত্যাদি) নির্বাচন করতে দেবে**  
✅ **সকল ভিডিও ডাউনলোড করার পর একটি ZIP ফাইলে সংরক্ষণ করবে**  
✅ **FFmpeg ইন্সটল করা না থাকলে অটো চেক করবে**  

---

## **🛠 প্রয়োজনীয় সফটওয়্যার:**  
1️⃣ **Python** ইন্সটল করুন [Python Download](https://www.python.org/downloads/)  
2️⃣ **yt-dlp** ইন্সটল করুন:  
   ```sh
   pip install yt-dlp
   ```
3️⃣ **FFmpeg** ইন্সটল করুন (ভিডিও + অডিও মিক্সিং এর জন্য)  

👉 **Windows এ FFmpeg ইন্সটল করার নিয়ম:**  
1. [FFmpeg Download](https://ffmpeg.org/download.html) থেকে Windows ভার্সন নামান  
2. Extract করে **C:\ffmpeg\bin** ফোল্ডারের পাথ **System Environment Variables** এ যুক্ত করুন  
3. Command Prompt খুলে চেক করুন:  
   ```sh
   ffmpeg -version
   ```  
   যদি আউটপুট দেখায় তাহলে ইন্সটল ঠিকমতো হয়েছে ✅  

👉 **Linux/macOS এ ইন্সটল:**  
```sh
sudo apt install ffmpeg   # Ubuntu/Debian  
brew install ffmpeg       # macOS  
```

---

## **📜 সম্পূর্ণ Python Script:**  
```python
import os
import shutil
import yt_dlp
import subprocess

# ✅ FFmpeg ইনস্টল চেক করার ফাংশন
def check_ffmpeg():
    try:
        subprocess.run(["ffmpeg", "-version"], stdout=subprocess.PIPE, stderr=subprocess.PIPE)
        return True
    except FileNotFoundError:
        return False

if not check_ffmpeg():
    print("❌ FFmpeg ইনস্টল করা নেই! অনুগ্রহ করে এটি ইন্সটল করুন এবং স্ক্রিপ্টটি পুনরায় চালান।")
    exit(1)

# ✅ ইউজারের ইনপুট নেওয়ার ফাংশন
def get_choice(prompt, choices):
    while True:
        print(prompt)
        for key, value in choices.items():
            print(f"{key}. {value}")
        choice = input("👉 আপনার পছন্দ লিখুন: ").strip()
        if choice in choices:
            return choices[choice]
        print("❌ ভুল ইনপুট! আবার চেষ্টা করুন।")

# ✅ ইউজার থেকে YouTube Playlist লিংক নেওয়া
playlist_url = input("📥 YouTube Playlist URL দিন: ").strip()

# ✅ ফরম্যাট সিলেকশন
format_options = {
    "1": "mp4",
    "2": "mkv"
}
format_choice = get_choice("🎥 ভিডিও ফরম্যাট নির্বাচন করুন:", format_options)

# ✅ ভিডিও কোয়ালিটি সিলেকশন
quality_options = {
    "1": "best",
    "2": "1080",
    "3": "720",
    "4": "480",
    "5": "360"
}
quality_choice = get_choice("📺 ভিডিও কোয়ালিটি নির্বাচন করুন:", quality_options)

# ✅ ডাউনলোড ফোল্ডার তৈরি
download_dir = 'YouTube_Playlist'
os.makedirs(download_dir, exist_ok=True)

# ✅ yt-dlp সেটিংস কনফিগার
ydl_opts = {
    'outtmpl': os.path.join(download_dir, '%(title)s.%(ext)s'),
    'format': f'bestvideo[ext={format_choice}][height<={quality_choice}]+bestaudio/best',
    'merge_output_format': format_choice,  # নির্দিষ্ট ফরম্যাট মেনে ফাইল সেভ করা
}

# ✅ ভিডিও ডাউনলোড শুরু
try:
    with yt_dlp.YoutubeDL(ydl_opts) as ydl:
        ydl.download([playlist_url])

    # ✅ ডাউনলোড ফাইল ZIP করা
    zip_filename = f"{download_dir}.zip"
    shutil.make_archive(download_dir, 'zip', download_dir)

    print(f'✅ ডাউনলোড সফল হয়েছে! ZIP ফাইল তৈরি করা হয়েছে: {zip_filename}')

except Exception as e:
    print(f'❌ সমস্যা হয়েছে: {e}')
```

---

## **💻 কিভাবে রান করবেন?**
1️⃣ **Python Script চালু করুন:**  
   ```sh
   python script.py
   ```
2️⃣ **আপনার YouTube Playlist লিংক দিন**  
3️⃣ **ভিডিও ফরম্যাট নির্বাচন করুন (MP4/MKV)**  
4️⃣ **ভিডিও কোয়ালিটি নির্বাচন করুন (1080p, 720p, ইত্যাদি)**  
5️⃣ **ভিডিও ডাউনলোড শুরু হবে & শেষে ZIP ফাইল তৈরি হবে**  

---

## **📌 স্ক্রিপ্ট কিভাবে কাজ করে?**
✅ **ইউজার থেকে YouTube Playlist লিংক ইনপুট নেয়**  
✅ **ভিডিও ফরম্যাট (MP4/MKV) ও কোয়ালিটি (1080p, 720p, ইত্যাদি) সিলেক্ট করতে দেয়**  
✅ **yt-dlp ব্যবহার করে ভিডিও ডাউনলোড করে**  
✅ **ডাউনলোড করা ফাইলগুলো ZIP আকারে সংরক্ষণ করে**  

---

## **🔥 Extra Tips:**
1️⃣ **Windows এ "ffmpeg not found" সমস্যা হলে:**  
   - ffmpeg ঠিকভাবে **System PATH** এ যুক্ত হয়েছে কিনা চেক করুন  
2️⃣ **ডাউনলোড স্পিড বাড়াতে:**  
   ```python
   'external_downloader': 'aria2c',
   'external_downloader_args': ['-x', '16', '-k', '1M']
   ```
   এগুলো **ydl_opts** এ যোগ করুন  
3️⃣ **একই নামের ভিডিও এভোয়েড করতে:**  
   ```python
   'outtmpl': os.path.join(download_dir, '%(title)s-%(id)s.%(ext)s')
   ```
   এতে প্রতিটি ভিডিও আলাদা নামে ডাউনলোড হবে ✅  

---

### **🎯 শেষ কথা**  
এই স্ক্রিপ্টটি **YouTube Playlist সহজেই ডাউনলোড ও ZIP করতে সাহায্য করবে**।  
**কোনো সমস্যা হলে কমেন্ট করুন! Happy Coding! 🚀**
