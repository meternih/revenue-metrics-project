# 📊 Revenue Metrics — Definitions / Пояснення метрик

## 🔹 MRR — Monthly Recurring Revenue / Щомісячний регулярний дохід
**Definition:** Total revenue from active subscriptions in a given month  
**Формула:** `SUM(mrr_usd)`  
**Пояснення:** Показує стабільний дохід, який компанія отримує щомісяця

---

## 🔹 Paid Users / Платні користувачі
**Definition:** Number of users with active paid subscriptions  
**Формула:** `COUNTD(IF mrr_usd > 0 THEN user_id END)`  
**Пояснення:** Визначає базу платних клієнтів

---

## 🔹 ARPPU — Average Revenue Per Paying User / Середній дохід на платного користувача
**Definition:** Average revenue per paying user  
**Формула:** `SUM(mrr_usd) / COUNTD(IF mrr_usd > 0 THEN user_id END)`  
**Пояснення:** Показує, скільки в середньому приносить один платний користувач

---

## 🔹 New MRR / Новий регулярний дохід
**Definition:** Revenue from first-time subscriptions  
**Формула:** `IF month = { FIXED user_id : MIN(month) } THEN mrr_usd END`  
**Пояснення:** Відображає нові підписки, які з’явились у поточному місяці

---

## 🔹 Churned Users / Втрачені користувачі
**Definition:** Users who canceled their subscription  
**Формула:** `COUNTD(IF is_churned_user = 1 THEN user_id END)`  
**Пояснення:** Показує кількість користувачів, які припинили платити

---

## 🔹 Churned Revenue / Втрачені доходи
**Definition:** Revenue lost due to churn  
**Формула:** `IF change_type = 'churn' THEN mrr_usd END`  
**Пояснення:** Скільки грошей втрачено через відтік

---

## 🔹 Churn Rate / Рівень відтоку
**Definition:** Percentage of users lost relative to total paid users  
**Формула:** `lookup_churn_user / paid_users`  
**Пояснення:** Відображає темп втрати користувачів

---

## 🔹 Revenue Churn Rate / Відтік доходу
**Definition:** Percentage of revenue lost due to churn  
**Формула:** `churned_revenue / mrr`  
**Пояснення:** Показує, наскільки сильно відтік впливає на загальний дохід

---

## 🔹 Expansion MRR / Дохід від апгрейдів
**Definition:** Additional revenue from users who upgraded  
**Формула:** `IF change_type = 'expansion' THEN mrr_usd END`  
**Пояснення:** Відображає зростання доходу через апгрейди

---

## 🔹 Contraction MRR / Зменшення доходу
**Definition:** Revenue lost due to downgrades  
**Формула:** `IF change_type = 'contraction' THEN mrr_usd END`  
**Пояснення:** Показує, наскільки зменшився дохід через даунгрейди

---

## 🔹 Customer Lifetime / Життєвий цикл клієнта
**Definition:** Average duration a user stays subscribed  
**Формула:** `1 / churn_rate`  
**Пояснення:** Вказує, скільки місяців в середньому користувач залишається платним

---

## 🔹 LTV — Lifetime Value / Цінність клієнта
**Definition:** Total expected revenue from a user over their lifetime  
**Формула:** `ARPPU * LT`  
**Пояснення:** Показує, скільки в середньому приносить один користувач за весь період підписки
