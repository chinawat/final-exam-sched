# Final exam scheduling system
Final exam scheduling system implemented using graph coloring algorithm.

## โครงสร้างไดเรกทอรีสำหรับข้อมูลนำเข้าของโปรแกรม

ข้อมูลนำเข้าของโปรแกรมต้องมีการจัดเก็บตามโครงสร้างไดเรกทอรี่และมีการตั้งชื่อไฟล์ดังที่แสดงด้านล่าง
```
📦final-exam-sched
 ┣ 📂data
 ┃ ┣ 📂exam-courses-faculty
 ┃ ┃ ┣ 📜01.in
 ┃ ┃ ┣ 📜02.in
 ┃ ┃ ┣ 📜03.in
 ┃ ┃ ┣ 📜04.in
 ┃ ┃ ┣ 📜05.in
 ┃ ┃ ┣ 📜06.in
 ┃ ┃ ┣ 📜07.in
 ┃ ┃ ┣ 📜08.in
 ┃ ┃ ┣ 📜09.in
 ┃ ┃ ┣ 📜10.in
 ┃ ┃ ┣ 📜11.in
 ┃ ┃ ┣ 📜12.in
 ┃ ┃ ┣ 📜13.in
 ┃ ┃ ┣ 📜14.in
 ┃ ┃ ┣ 📜15.in
 ┃ ┃ ┣ 📜16.in
 ┃ ┃ ┣ 📜17.in
 ┃ ┃ ┣ 📜18.in
 ┃ ┃ ┣ 📜19.in
 ┃ ┃ ┣ 📜20.in
 ┃ ┃ ┗ 📜21.in
 ┃ ┣ 📜all-exam-course.in
 ┃ ┣ 📜conflicts.in
 ┃ ┣ 📜enrolled-courses.in
 ┃ ┣ 📜faculty-capacity.in
 ┃ ┣ 📜regist-studentid.in
 ┃ ┗ 📜regist.in
 ┣ 📜final_exam_graph_coloring.py
 ┣ 📜penalty_calc.py
 ┣ 📜start_penalty_report.py
 ┣ 📜start_scheduler.py
 ┗ 📜std_data_to_json.py
```
## คำอธิบายโครงสร้างและรูปแบบข้อมูลในแต่ละไฟล์
-   ในโฟลเดอร์ data ประกอบไปด้วยไฟล์ all-exam-course.in,
    faculty-capacity.in, conflicts.in, enrolled-courses.in, regist.in,
    regist-studentid.in รวมทั้งหมดจำนวน 6 ไฟล์ แต่ละไฟล์ เป็นไฟล์ text

-   ในไฟล์ all-exam-course.in แต่ละบรรทัดประกอบด้วย
    &lt;รหัสวิชาที่มีการจัดสอบ&gt; หนึ่งบรรทัดต่อหนึ่งรหัสวิชา
    ตัวอย่างดังภาพ
    <p align="center">
     <img src="./readme_image/all_exam1.png?raw=true" alt="All_courses"/>
    </p>

-   ในไฟล์ faculty-capacity.in แต่ละบรรทัดประกอบด้วย
    รหัสคณะและจำนวนความจุรวมของห้องสอบของคณะนั้น ๆ มีรูปแบบดังนี้
    &lt;รหัสคณะ&gt; &lt;ความจุห้องสอบคณะ&gt; แต่ละส่วนคั่นด้วย เว้นวรรค
    (space) หนึ่งบรรทัดต่อหนึ่งคณะ
    ตัวอย่างดังภาพ
    <p align="center">
     <img src="./readme_image/capacity1.png?raw=true" alt="Capacity"/>
    </p>

-   ในไฟล์ conflicts.in แต่ละบรรทัดประกอบด้วย
    รหัสวิชาสองวิชาที่มีนักศึกษาลงทะเบียนพร้อมกันในภาคการศึกษานั้น ๆ และ
    จำนวนนักศึกษาที่ลงทะเบียนคู่วิชานี้ มีรูปแบบดังนี้ &lt;รหัสวิชา&gt;
    &lt;รหัสวิชา&gt; &lt;จำนวนนักศึกษา&gt; แต่ละส่วนคั่นด้วย เว้นวรรค
    (space) ตัวอย่างดังภาพ
    <p align="center">
     <img src="./readme_image/conflicts1.png?raw=true" alt="Conflicts"/>
    </p>

-   ในไฟล์ enrolled-courses.in แต่ละบรรทัดประกอบด้วย
    รหัสวิชาและจำนวนนักศึกษาที่ลงทะเบียนในวิชานั้น ๆ  
    มีรูปแบบดังนี้ &lt;รหัสวิชา&gt; &lt;จำนวนนักศึกษา&gt;
    แต่ละส่วนคั่นด้วย เว้นวรรค (space)
    ตัวอย่างดังภาพ
    <p align="center">
     <img src="./readme_image/courses1.png?raw=true" alt="Enrolled courses"/>
    </p>
    
-   ในโฟลเดอร์ data/exam-courses-faculty ประกอบไปด้วยไฟล์ 01.in ถึง
    21.in ซึ่งเป็นไฟล์ text โดยตั้งชื่อไฟล์ตามรหัสคณะ
    ในแต่ละไฟล์ประกอบด้วย รหัสวิชาที่มีการจัดสอบ
    หนึ่งบรรทัดต่อหนึ่งรหัสวิชา
    ตัวอย่างดังภาพ
    <p align="center">
     <img src="./readme_image/all_exam1.png?raw=true" alt="All_courses"/>
    </p>

-   ในไฟล์ regist.in แต่ละบรรทัดประกอบด้วย
    ข้อมูลลงทะเบียนของนักศึกษาหนึ่งคน
    ประกอบด้วยด้วยรหัสวิชาทั้งหมดที่นักศึกษาคนนั้นลงทะเบียน
    มีรูปแบบดังนี้ &lt;รหัสวิชา&gt; &lt;รหัสวิชา&gt; &lt;รหัสวิชา&gt;
    ... แต่ละวิชาคั่นด้วย เว้นวรรค (space)
    ตัวอย่างดังภาพ
    <p align="center">
     <img src="./readme_image/regist1.png?raw=true" alt="Regist"/>
    </p>

-   ในไฟล์ regist-studentid.in แต่ละบรรทัดประกอบด้วย ข้อมูลลงทะเบียนของนักศึกษาหนึ่งคน  
    ซึ่งประกอบด้วยด้วยรหัสนักศึกษาและวิชาทั้งหมดที่นักศึกษาคนนั้นลงทะเบียน
    มีรูปแบบดังนี้  
    &lt;รหัสนักศึกษา&gt; &lt;รหัสวิชา&gt; &lt;รหัสวิชา&gt;
    &lt;รหัสวิชา&gt; ... แต่ละส่วนคั่นด้วย เว้นวรรค (space)  ตัวอย่างดังภาพ
    <p align="center">
     <img src="./readme_image/regist_hashed.png?raw=true" alt="Regist_hashed"/>
    </p>


## วิธีการใช้งานโปรแกรม

1.  จัดเตรียมไฟล์ข้อมูลนำเข้าต่าง ๆ ตามที่ได้ระบุไว้ใน
    [โครงสร้างไดเรกทอรีสำหรับข้อมูลนำเข้าของโปรแกรม][1] ให้เรียบร้อย

2.  เปิดไฟล์ final\_exam\_graph\_coloring.py

3.  ทำการแก้ไข path ของไฟล์ข้อมูลนำเข้าต่าง ๆ ให้ตรงตามที่กำหนด
    หากได้ตั้งชื่อไฟล์ และจัดแยกไฟล์ต่าง ๆ
    ไว้ตามโฟลเดอร์ที่กำหนดแล้วไม่จำเป็นต้องแก้ไขตัวแปร path ใด ๆ

4.  ทำการแก้ไขจำนวน slot ที่ใช้สอบ โดยแก้ไขที่ตัวแปร TOTAL\_SLOTS

ในกรณีที่ต้องการจัดตารางสอบด้วยอัลกอริทึมเพียงวิธีเดียว
สามารถเรียกใช้งานโปรแกรมผ่าน console หรือ terminal เช่น cmd หรือ
powershell ได้ด้วยคำสั่ง
```
py final_exam_graph_coloring.py [-OPTION]
```
ซึ่ง OPTION มีทั้งหมด 4 OPTION ได้แก่ \[-deg, -std, -deg-bfs, -std-bfs\]

#### ตัวอย่างการเรียกใช้งานโปรแกรม
```      
py final_exam_graph_coloring.py -deg
```
ในกรณีที่ต้องการจัดตารางสอบทั้งหมด 4 วิธี สามารถเรียกใช้งานโปรแกรมผ่าน
console หรือ terminal เช่น cmd หรือ powershell ได้ด้วยคำสั่ง
```
py start_scheduler.py
```

## วิธีการใช้งานโปรแกรมคำนวณค่า penalty

1.  จัดเตรียมไฟล์ข้อมูลนำเข้าต่าง ๆ ตามที่ได้ระบุไว้ใน
    [โครงสร้างไดเรกทอรีสำหรับข้อมูลนำเข้าของโปรแกรม][1] ให้เรียบร้อย

2.  เปิดไฟล์ penalty\_calc.py

3.  ทำการแก้ไข path ของไฟล์ข้อมูลนำเข้าต่าง ๆ ให้ตรงตามที่กำหนด
    หากได้ตั้งชื่อไฟล์ และจัดแยกไฟล์ต่าง ๆ
    ไว้ตามโฟลเดอร์ที่กำหนดแล้วไม่จำเป็นต้องแก้ไขตัวแปร path ใด ๆ

4.  ทำการแก้ไขจำนวน slot ที่ใช้สอบให้ตรงกับ solution
    ของตารางสอบที่จัดโดยโปรแกรม โดยแก้ไขที่ตัวแปร TOTAL\_SLOTS

ในกรณีที่ต้องการคิดคำนวณค่า penalty ของตารางสอบเพียง 1 solution
สามารถเรียกใช้งานโปรแกรมผ่าน console หรือ terminal เช่น cmd หรือ
powershell ได้ด้วยคำสั่ง
```
py penalty_calc.py <solution_file>
```
โดยที่ &lt;solution\_file&gt; คือ path ของไฟล์ solution
ตารางสอบที่ได้จากโปรแกรมจัดตารางสอบ

#### ตัวอย่างการเรียกใช้งานโปรแกรมคำนวณค่า penalty
```
py penalty_calc.py solution/graph-coloring-solution-deg.txt
```
ในกรณีที่ต้องการคิดคำนวณค่า penalty ของตารางสอบทั้งหมด 4 วิธี
สามารถเรียกใช้งานโปรแกรมคำนวณค่า penalty ผ่าน console หรือ terminal เช่น
cmd หรือ powershell ได้ด้วยคำสั่ง
```
py start_penalty_report.py
```
โดยให้เปิดไฟล์ start\_penalty\_report.py เพื่อแก้ไขตัวแปร
solution\_folder ให้ชี้ไปยังโฟลเดอร์ที่เก็บ solution
ตารางสอบทั้งหมดที่เป็น output
ของโปรแกรมจัดตารางสอบให้ถูกต้องก่อนการเรียกใช้งานคำสั่งด้านบน

  [1]: โครงสร้างไดเรกทอรีสำหรับข้อมูลนำเข้าของโปรแกรม
