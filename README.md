## 📌 Project Overview

This dashboard analyses **705 students from 110 countries** to understand how daily social media use connects with sleep, mental health, academic performance and relationships.

Built as part of the *Data Analytics with GenAI* programme (Career247).

---

## ✨ Interactive Features

| Feature | How it is used |
| ------- | -------------- |
| 🔖 **Bookmarks** | On the *Interactive Story View* page, two buttons switch between **Gender View** and **Academic Level View** |
| 🔍 **Drill-through** | Right-click a student on the table and drill through to the **Student Profile** page for that student's full details |
| 🎚️ **Slicers** | Filter by Gender, Age, Country and Academic Level |
| 📊 **DAX Measures** | Average usage, average sleep, % affected academically and more |

---

## 📄 Dashboard Pages

| # | Page | What it shows |
| - | ---- | ------------- |
| 1 | **Executive Overview** | Total students, average usage, average sleep, % affected academically |
| 2 | **Mental Health & Lifestyle** | Health band by country, addiction vs mental health, sleep by age |
| 3 | **Academic Impact** | Usage by academic level, academic impact by platform |
| 4 | **Relationships & Conflicts** | Conflict level by relationship status, student-wise addiction table |
| 5 | **Interactive Story View** | Gender View and Academic Level View (bookmarks) |
| 6 | **Student Profile** | Drill-through page with one student's full details |

---

## 🗂️ Dataset

Excel file: `data/Students_Social_Media_Addiction.xlsx`

| Sheet | Columns |
| ----- | ------- |
| **Student Details** | Student_ID, Age, Gender, Academic_Level, Country, Sleep_Hours_Per_Night, Mental_Health_Score, Relationship_Status, Conflicts_Over_Social_Media, Addicted_Score |
| **Platform Details** | Student_ID, Avg_Daily_Usage_Hours, Most_Used_Platform, Affects_Academic_Performance |

Both sheets are connected using `Student_ID` (one-to-one relationship).

---

## 🧮 DAX Used

```DAX
Health Band = IF(Mental_Health_Score >= 7, "Good",
                 IF(Mental_Health_Score >= 4, "Average", "Poor"))

Conflict Level = SWITCH(TRUE(),
                        Conflicts_Over_Social_Media > 5, "High",
                        Conflicts_Over_Social_Media > 2, "Medium",
                        "Low")

Avg Sleep Hours = AVERAGE(Student_Details[Sleep_Hours_Per_Night])

Avg Usage Hours = AVERAGE(Platform_Details[Avg_Daily_Usage_Hours])

% Affected Academically =
    DIVIDE(
        CALCULATE(COUNTROWS(Platform_Details),
                  Platform_Details[Affects_Academic_Performance] = "Yes"),
        COUNTROWS(Platform_Details))
```

---

## 💡 Key Insights

* ⏱️ Students spend about **4.9 hours** a day on social media and sleep about **6.9 hours**.
* 🎓 About **64%** of students say social media affects their studies.
* 📸 **Instagram** is the most used platform, followed by TikTok and Facebook.
* 😴 Higher usage goes with **less sleep** and **lower mental health scores**.
* 🏫 **High school** students have the highest usage and addiction score.

> These are patterns in survey data, not proof of cause and effect.

---

## 🚀 How to Open

1. Install the free **Power BI Desktop**.
2. Download `Students_Social_Media_Addiction_Dashboard.pbix` and open it.
3. If asked, point the data source to `data/Students_Social_Media_Addiction.xlsx`.

---

## 👤 Author

**Avinash Thapa**
Data Analyst Portfolio Project
🔗 [GitHub: avinashanalyst2000](https://github.com/avinashanalyst2000)
