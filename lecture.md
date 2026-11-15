
# Python Web Scraping & regular expression

- เซฟข้อมูลจากเว๊บไซต์
-

## Outline

1) What is Web Scraping 
2) Intro to HTML3
3) Web Scraping with Requests and Python Beautiful Soup 
4) Using Selenium to handle AJAX & JavaScript driven web pages
5) Regular expressions with Python
6) Real World Example(Pantip.com)
   
____ 

### 1) What is Web Scraping

- การดึงข้อมูลจากเว๊บ 

- เพราะข้อมูลที่เราต้องการบนเว๊บอาจจะไม่ได้ open data หรือ train model ยาก เราจึงต้องไปแกะเอง หรือ api ที่มีให้ อาจติด limit หรือได้ไม่ครบตามที่เราต้องการ

- สกัดมาจัดรูปแบบใหม่ แล้วแปลงมาเป็นรูปแบบที่เราต้องการ เช่น json, csv เป็นต้น

- อาจจะข้อมูลจากรัฐ รพ. รร. , online pantip หรือ wongnai  -> ดูว่าลูกค้าต้องการอะไร , ข่าว งบการเงิน นำมาวิเคราะห์ 


แนบรูปสองรูป

#### รูปแบบการทำงานของ website


1) Static Site Render

แนบรูป 

- เปิดเว๊บมาแล้วเอาข้อมูลได้เลย ดูดง่าย
- ข้อเสีย : ux ไม่ดี เปิดหน้าอื่นต้องโหลดใหม่ทั้งหน้า

2) Client Side Rendering

แนบรูป 

- ไปหน้าอื่นจะดึงแค่ข้อมูลที่เราต้องการ ux ดี
- ยากในการดึงข้อมูล จะได้แต่ JS แทน ข้อความ
- เว๊บไทยชนะ

3) Server Side Rendering 

แนบรูป 

- เปิดมา เจอเนื้อหาที่เราต้องการ แต่ไม่ใช่ทั้งหมด อาจจะทำไรสักอย่างกับเว๊บ


