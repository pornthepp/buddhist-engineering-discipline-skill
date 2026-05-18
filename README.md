# Buddhist Engineering Discipline Skill

Claude Code Skill สำหรับเตือน AI Agent ให้ทำงานแบบ:

- ตรวจสอบก่อนเชื่อ
- หา root cause ก่อนแก้
- เช็ก state ล่าสุดก่อนทำ
- ไม่ยึดติด draft แรก
- ไม่ซ่อนบั๊กด้วย workaround เปราะ ๆ
- ตั้งมั่นกับหลักฐานเมื่อโดน push หรือ tool fail
- ตอบแบบซื่อสัตย์ ใช้งานได้จริง และตรวจสอบก่อนส่ง

---

## Files

```text
.claude/
  skills/
    buddhist-engineering-discipline/
      SKILL.md
      reference.md
      debug-checklist.md
      examples.md
```

---

## Install

นำโฟลเดอร์ `.claude` ไปวางไว้ที่ root ของโปรเจกต์ที่ใช้ Claude Code

ตัวอย่าง:

```text
your-project/
  .claude/
    skills/
      buddhist-engineering-discipline/
        SKILL.md
        reference.md
        debug-checklist.md
        examples.md
```

---

## Design

`SKILL.md` ถูกเขียนให้สั้นและเป็น behavior rules เพื่อประหยัด token

ไฟล์เสริม:

- `reference.md` ใช้เมื่อต้องการอ่านที่มาของหลักธรรมและ mapping ภาษาไทย
- `debug-checklist.md` ใช้เฉพาะงาน debug, SQL, PL/SQL, API, config, build, JasperReports, runtime error
- `examples.md` ใช้เมื่อต้องการตัวอย่างพฤติกรรมก่อน/หลัง

---

## Recommended use

ใช้ skill นี้กับงาน:

- PL/SQL / SQL
- Java / Spring Boot
- Angular
- JasperReports
- Debugging
- Refactoring
- Code review
- Architecture / requirement analysis
- งานที่ข้อมูลอาจเปลี่ยนและต้อง verify
