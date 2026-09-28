# GitHub Projects Setup Guide

คู่มือการตั้งค่า GitHub Projects พร้อม Custom Fields สำหรับ Sprint Planning

## วิธีสร้าง GitHub Project

### ขั้นตอนที่ 1: สร้าง Project ใหม่

1. ไปที่ repository ของคุณบน GitHub
2. คลิกแท็บ **Projects**
3. คลิก **New project**
4. เลือก template หรือเริ่มต้นด้วย **Table** view
5. ตั้งชื่อ Project (เช่น "Sprint Board" หรือ "Sprint Planning")

### ขั้นตอนที่ 2: เพิ่ม Custom Fields

#### 1. Sprint / Iteration Field
- คลิก **+** ข้างหัวคอลัมน์
- เลือก **New field**
- Field name: `Sprint`
- Field type: **Iteration**
- กำหนด:
  - Iteration duration (เช่น 2 weeks)
  - Start date
  - จำนวน iterations ที่ต้องการสร้างล่วงหน้า

#### 2. Start Date Field
- คลิก **+** ข้างหัวคอลัมน์
- Field name: `Start Date`
- Field type: **Date**

#### 3. Target Date Field
- คลิก **+** ข้างหัวคอลัมน์
- Field name: `Target Date`
- Field type: **Date**

#### 4. Estimate Field
- คลิก **+** ข้างหัวคอลัมน์
- Field name: `Estimate`
- Field type: **Number**
- Description: "Estimated hours"

#### 5. Actual Field
- คลิก **+** ข้างหัวคอลัมน์
- Field name: `Actual`
- Field type: **Number**
- Description: "Actual hours spent"

### ขั้นตอนที่ 3: ตั้งค่า Default Fields

GitHub Projects มี built-in fields อยู่แล้ว:
- **Status** (Todo, In Progress, Done)
- **Priority** (Low, Medium, High, Urgent)
- **Assignees**
- **Labels**

### ขั้นตอนที่ 4: เชื่อม Issues กับ Project

#### วิธีที่ 1: Auto-add (แนะนำ)
1. ไปที่ Project Settings (คลิก **...** มุมขวาบน → **Settings**)
2. ใน **Workflows** section
3. เปิด "Auto-add to project"
4. กำหนดเงื่อนไข (เช่น issues ทั้งหมดใน repo นี้)

#### วิธีที่ 2: Manual add
- ใน issue form คุณสามารถระบุ project ได้ใน frontmatter:
```yaml
projects: ["username/repository/1"]
```

## การใช้งาน

### สร้าง Issue ใหม่
1. ไปที่ **Issues** → **New issue**
2. เลือก **Sprint Task** template
3. กรอกข้อมูล Sprint, dates, estimate
4. Submit issue

### อัปเดต Custom Fields ใน Project Board
1. ไปที่ Project Board
2. คลิกที่ cell ในคอลัมน์ที่ต้องการแก้ไข
3. กรอกหรืออัปเดตค่า (เช่น เลือก Sprint iteration, ใส่วันที่, กรอกตัวเลข)

### Views ที่แนะนำ

#### Sprint Board View (Table)
แสดงทุก field พร้อมกัน เหมาะสำหรับ planning

#### Kanban View (Board)
- Group by: Status
- Filter: Current Sprint
- เหมาะสำหรับ daily standup

#### Timeline View
- แสดง tasks ตามช่วงเวลา (Start Date → Target Date)
- เหมาะสำหรับดู sprint timeline

## Tips & Best Practices

1. **ตั้งค่า Automation**
   - Auto-close issues เมื่อ Status = Done
   - Auto-assign sprint เมื่อสร้าง issue ใหม่

2. **สร้าง Views หลายแบบ**
   - Current Sprint (filter: Sprint = current)
   - Backlog (filter: Sprint = null)
   - Completed (filter: Status = Done)

3. **Track Burndown**
   - ใช้ Insights tab เพื่อดู burndown chart
   - เปรียบเทียบ Estimate vs Actual

4. **Integration with Issue Forms**
   - ข้อมูลจาก issue form จะไปอยู่ใน issue body
   - Custom fields ใน Projects ต้องกรอกใน Project Board
   - พิจารณาใช้ GitHub Actions เพื่อ sync ข้อมูลอัตโนมัติ

## ตัวอย่าง Workflow

1. Product Owner สร้าง issues จาก template (Sprint Task)
2. Team นำ issues เข้า Sprint Board
3. กำหนด Sprint iteration และ estimates
4. ระหว่าง sprint อัปเดต Status และ Actual hours
5. Review sprint metrics ที่จบ sprint

## เอกสารเพิ่มเติม

- [About Projects](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects)
- [Custom fields in Projects](https://docs.github.com/en/issues/planning-and-tracking-with-projects/understanding-fields)
- [Automating Projects](https://docs.github.com/en/issues/planning-and-tracking-with-projects/automating-your-project)
