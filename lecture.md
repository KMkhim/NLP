
# Python Web Scraping & regular expression


## Outline

1) What is Web Scraping 
2) Intro to HTML3
3) Web Scraping with Requests and Python Beautiful Soup 
4) Using Selenium to handle AJAX & JavaScript driven web pages
5) Regular expressions with Python
6) Real World Example(Pantip.com)
   
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


