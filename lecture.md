
# Python Web Scraping & regular expression


## Outline

1) What is Web Scraping 
2) Intro to HTML3
3) Web Scraping Workflow
4) Web Scraping with Requests and Python Beautiful Soup 
5) Using Selenium to handle AJAX & JavaScript driven web pages
6) Regular expressions with Python
7) Real World Example(Pantip.com)
   
____ 

### 1) What is Web Scraping

<img width="720" height="262" alt="Screenshot 2569-11-15 at 13 16 26" src="https://github.com/user-attachments/assets/469d7328-4fe4-4165-8aef-aa2b39dea4a6" />

- การดึงข้อมูลจากเว๊บ 

- เพราะข้อมูลที่เราต้องการบนเว๊บอาจจะไม่ได้ open data หรือ train model ยาก เราจึงต้องไปแกะเอง หรือ api ที่มีให้ อาจติด limit หรือได้ไม่ครบตามที่เราต้องการ

- สกัดมาจัดรูปแบบใหม่ แล้วแปลงมาเป็นรูปแบบที่เราต้องการ เช่น json, csv เป็นต้น

- อาจจะข้อมูลจากรัฐ รพ. รร. , online pantip หรือ wongnai  -> ดูว่าลูกค้าต้องการอะไร , ข่าว งบการเงิน นำมาวิเคราะห์ 


<img width="745" height="349" alt="Screenshot 2569-11-15 at 13 16 52" src="https://github.com/user-attachments/assets/aa6a36fa-5acb-4d80-ac43-b86f6f75c964" />


#### รูปแบบการทำงานของ website 


**1) Static Site Render**

<img width="744" height="322" alt="Screenshot 2569-11-15 at 13 17 14" src="https://github.com/user-attachments/assets/d5390a9e-de4d-45ba-a3bb-c582c37e1e79" />

- เปิดเว็บมาแล้วเอาข้อมูลได้เลย ดูดง่าย
- ข้อเสีย : ux ไม่ดี เปิดหน้าอื่นต้องโหลดใหม่ทั้งหน้า

**2) Client Side Rendering** 

<br>

<img width="656" height="315" alt="Screenshot 2569-11-15 at 13 17 51" src="https://github.com/user-attachments/assets/36a7bc72-af55-42f0-aa34-4441956e6c37" />

<br>
<br>


- ไปหน้าอื่นจะดึงแค่ข้อมูลที่เราต้องการ ux ดี
- ยากในการดึงข้อมูล จะได้แต่ JS แทน ข้อความ
- ตัวอย่าง : เว็บไทยชนะ 
  

**3) Server Side Rendering**

<img width="619" height="423" alt="Screenshot 2569-11-15 at 13 18 01" src="https://github.com/user-attachments/assets/fe1a6319-418a-4b62-82a6-a0fdd3b1f3e5" />

<br>


- เปิดมา เจอเนื้อหาที่เราต้องการ แต่ไม่ใช่ทั้งหมด อาจจะต้องทำไรสักอย่างกับเว็บ
____ 

### 2)  Intro to HTML3

<br>


 <img width="704" height="422" alt="Screenshot 2569-11-15 at 14 04 01" src="https://github.com/user-attachments/assets/9a2ccf45-cdba-479b-ae5b-fb3e7da1ce8b" />

 <br>

<img width="749" height="366" alt="Screenshot 2569-11-15 at 14 04 12" src="https://github.com/user-attachments/assets/ff6c543e-3366-44ba-8566-8e446fb0f0e0" />

<br>

- ภาษาที่ใช้ทำเว็บ หรือแสดงผล
- tag p เปิด ปิด 1 พารากราฟ :
  - Attribute กำหนดคุณสมบัติให้กับ tag
  - class  เพื่อนำไปจัดรูปแบบ (Styling) หรือควบคุมด้วย JavaScript
  - id : ชื่อแท็ก
 
 

____ 

### 3)  Web Scraping Workflow

<img width="753" height="382" alt="Screenshot 2569-11-15 at 14 04 24" src="https://github.com/user-attachments/assets/6bf9af0f-452f-42b6-8e3b-be70634410d8" />

**1) Get the Website**

- ดูดหน้าเว็บ อาจะใช้ library python : urllib หรือ Requests
- ซึ่งมันจะได้ก้อนไฟล์ 1 ก้อน
- ข้อมูลที่ได้จะเป็นแค่ ข้อความดิบยาวๆ (Raw HTML String) ที่โปรแกรมยังแยกไม่ออกว่าอันไหนคือหัวข้อ อันไหนคือราคา

<img width="753" height="415" alt="Screenshot 2569-11-15 at 14 04 39" src="https://github.com/user-attachments/assets/e8ebb363-8914-4cf1-9d33-00325f45f08f" /> 

**2) Parse (แปลงโครงสร้างเพื่อค้นหา)**

- การจัดรูปแบบก้อนไฟล์ในรูปแบบที่เหมาะสม เช่น tree
- แปลง Raw HTML String ให้เป็นโครงสร้าง Tree (DOM Tree) เพื่อให้โค้ดไต่หาข้อมูลได้
- library : BeautifulSoup/Selenium/Scrapy

**BeautifulSoup**

- รับข้อความดิบมาทำเป็น Tree Object (ที่เรามักตั้งชื่อตัวแปรว่า soup) เพื่อให้เราไต่กิ่งก้านไปหยิบข้อมูลได้ง่ายๆ

<img width="552" height="266" alt="Screenshot 2569-11-15 at 14 05 22" src="https://github.com/user-attachments/assets/c9e8d1c3-d930-472f-9e2e-d5a864f20aeb" />

- อยากดึง tag , Attb, หรือแท็ก id สามารถใส่คำศัพทย์ตรงๆ
- โยน html แล้วหาตรงๆได้เลย
- คำสั่ง find : หา element แรก , find_all ได้มาเป็น list ถ้ามีหลาย output

  
<img width="554" height="323" alt="Screenshot 2569-11-15 at 14 05 36" src="https://github.com/user-attachments/assets/0983c82e-bb6b-4c12-bf56-0211d3fde5ee" />

**3) Extract & Store (ดึงค่าและจัดเก็บ)**

- หยิบเฉพาะข้อมูลที่ต้องการออกจาก Tree แล้วแปลงเป็นรูปแบบที่ใช้งานต่อได้ เช่น Table (CSV, Excel) หรือ JSON










