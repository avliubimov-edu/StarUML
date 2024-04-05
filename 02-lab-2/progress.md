# Ход выполнения

## Создание диаграммы Последовательности

1. Щелкните правой кнопкой мыши на `LAB_ISIT`.
2. В открывшемся меню выберите пункт Add Diagram | Sequence Diagram.
3. Переименуйте `Collaboration1` в `Lab2.Interactions`.
4. Переименуйте `SequenceDiagram1` в `Enter new order`.
5. Дважды щелкнув на этой диаграмме, откройте ее.

### Добавление на диаграмму действующего лица и объектов

1. Перетащите действующее лицо Sales person (Продавец) из [браузера ](../00-staruml-overview/polzovatelskii-interfeis.md#model-explorer)на диаграмму.
2. Нажмите кнопку Life Line на панели инструментов.
3. Щелкните мышью в верхней части диаграммы, чтобы поместить туда новый объект.
4. Назовите объект Order Options Form (Выбор варианта заказа).
5. Повторив шаги 3 и 4, поместите на диаграмму объекты:
   * Order Detail Form (Форма деталей заказа)
   * Order N1234 (Заказ № 1234)

### Добавление сообщений на диаграмму

1. На панели инструментов нажмите кнопку Message (Сообщение).
2. Проведите мышью от [линии жизни](#user-content-fn-1)[^1] действующего лица [Sales Person](#user-content-fn-2)[^2] к линии жизни объекта [Order Options Form](#user-content-fn-3)[^3].
3. Выделив сообщение, введите его имя — [Create new order](#user-content-fn-4)[^4].
4. Повторив шаги 2 и 3, поместите на диаграмму сообщения:&#x20;
5. [Open form](#user-content-fn-5)[^5] — между Order Options Form и [Order Detail Form](#user-content-fn-6)[^6]
6. [Enter order number, customer, order items](#user-content-fn-7)[^7] — между Salesperson и Order Detail Form
7. [Save the order](#user-content-fn-8)[^8] — между Salesperson и Order Detail Form
8. [Create new, blank order](#user-content-fn-9)[^9] () — между Order Detail Form и Order N1234&#x20;
9. Set the order number, customer, order items (Ввести номер заказа, заказчика и число заказываемых предметов) —между Order Detail Form и Order N1234
10. [Save the order](#user-content-fn-10)[^10]— между Order Detail Form и Order N1234&#x20;

Теперь нужно позаботиться об управляющих объектах и о взаимодействии с базой данных. Как видно из диаграммы, объект Order Detail Form имеет множество ответственностей, с которыми лучше всего мог бы справиться управляющий объект. Кроме того, новый заказ должен сохранять себя в базе данных сам. Вероятно, эту обязанность лучше было бы переложить на другой объект.

### Добавление на диаграмму дополнительных объектов

1. Нажмите кнопку Life Line на панели инструментов.
2. Щелкните мышью между объектами Order Detail Form и Order N1234, чтобы поместить туда новый объект.
3. Введите имя объекта — [Order Manager](#user-content-fn-11)[^11].
4. Нажмите кнопку Life Line панели инструментов.
5. Новый объект расположите справа от Order N1234.
6. Введите его имя —[Transaction Manager](#user-content-fn-12)[^12].

### Назначение ответственностей объектам

1. Выделите сообщение 5: [Create new, blank order](#user-content-fn-13)[^13].
2. Удалите это сообщение.
3. Повторите шаги 1 и 2 для удаления двух последних сообщений:
   * &#x20;Set the order number, customer, order items
   * Save the order
4. Нажмите кнопку Message панели инструментов.
5. Поместите на диаграмму новое сообщение, расположив его под сообщением 4 между Order Detail Form и Order Manager.
6. Назовите его [Save the order](#user-content-fn-14)[^14].
7. Повторите шаги 4—6, добавив сообщения с шестого по девятое и назвав их:&#x20;
   * [Create new, blank order](#user-content-fn-15)[^15] — между Order Manager и Order N1234
   * [Set the order number, customer, order items](#user-content-fn-16)[^16] — между Order Manager и Order N1234
   * [Save the order](#user-content-fn-17)[^17] —  между Order Manager и Transaction Manager
   * [Collect order information](#user-content-fn-18)[^18] —между Transaction Manager и Order N1234
8. &#x20;На панели инструментов нажмите кнопку Self Message  (Сообщение себе).&#x20;
9. Щелкните на линии жизни объекта Transaction Manager (Управляющий транзакциями) ниже сообщения 9, добавив туда рефлексивное сообщение.&#x20;
10. Назовите его Save the order information to the database (Сохранить информацию о заказе в базе данных).

### Соотнесение объектов с классами

1. Два раза кликните левой кнопкой мыши на объекте Order Options Form (Выбор варианта заказа).
2. Среди появившихся пиктограмм найдите Create Type
3. В поле введите OrderOptions (Выбор заказа)
4. Щелкните на кнопке ОК, чтобы вернуться к диаграмме. Теперь объект называется Order Options Form : OrderOptions.
5. Для соотнесения остальных объектов с классами повторите шаги с 1 по 4:
   * Тип OrderDetail соотнесите с объектом Order Detail Form
   * Тип OrderMgr — с объектом Order Manager
   * Тип Order — с объектом Order N1234
   * Тип TransactionMgr — с объектом Transaction Manager.

### Соотнесение сообщений с операциями

1. Два раза кликните левой кнопкой мыши на сообщении 1: Create new order (Создать новый заказ).
2. Среди появившихся пиктограмм найдите Create Operation
3. В поле Name введите имя операции — Create (Создать)
4. Повторите шаги с 1 по 3, чтобы соотнести с операциями все остальные сообщения:
   * Сообщение 2: Open form (Открыть форму) соотнесите с операцией Open()&#x20;
   * Сообщение 3: Enter order number, customer, order items (Ввести номер заказа, заказчика и число заказываемых предметов) — с операцией Submitlnfo()
   * Сообщение 4: Save the order (Сохранить заказ) — с операцией Save()&#x20;
   * Сообщение 5: Save the order (Сохранить заказ) — с операцией SaveOrder()
   * Сообщение 6: Create new, blank order (Создать пустой заказ) —с операцией Create()
   * Сообщение 7: Set the order number, customer, order items (Ввести номер заказа, заказчика и число заказываемых предметов) — с операцией Setlnfo()
   * Сообщение 8: Save the order (Сохранить заказ) — с операцией SaveOrder()&#x20;
   * Сообщение 9: Collect order information (Информация о заказе)  — с операцией Getlnfo()
   * Сообщение 10: Save the order information to the database (Сохранить информацию о заказе в базе данных) — с операцией Commit()

## Создание Кооперативной диаграммы

1. Щелкните правой кнопкой мыши на `Lab2.Interactions` в браузере.
2. В открывшемся меню выберите пункт Add Diagram | Communication Diagram (Создать | Кооперативная диаграмма).
3. Назовите эту диаграмму `Enter new order`.
4. Дважды щелкнув мышью на диаграмме, откройте ее.

### Добавление действующего лица и объектов на диаграмму

1. Перетащите действующее лицо Salesperson (Продавец) из браузера на диаграмму.
2. Нажмите кнопку Life Line панели инструментов.
3. Щелкните мышью где-нибудь внутри диаграммы, чтобы поместить туда новый объект.
4. Назовите объект Order Options Form.
5. Повторив шаги 3 и 4, поместите на диаграмму объекты:
   1. Order Detail Form (Форма деталей заказа)&#x20;
   2. Order N1234 (Заказ №1234)

### Добавление сообщений на диаграмму

1. На панели инструментов нажмите кнопку Connector (Соединитель).
2. Проведите мышью от действующего лица Salesperson (Продавец) к объекту Order Options Form (Выбор варианта заказа).
3. Повторите шаги 1 и 2, соединив связями следующие объекты:&#x20;
   * Действующее лицо Salesperson и объект Order Detail Form&#x20;
   * Объект Order Options Form и объект Order Detail Form
   * Объект Order Detail Form и объект Order N1234
4. На панели инструментов нажмите кнопку Forward Message (Прямое Сообщение).
5. Щелкните мышью на связи между Salesperson и Order Options Form.
6. Выделив сообщение, введите его имя —Create new order (Создать новый заказ).
7. Повторив шаги с 4 по 6, поместите на диаграмму сообщения:
   * Open form (Открыть форму) — между Order Options Form и Order Detail Form&#x20;
   * Enter order number, customer, order items (Ввести номер заказа, заказчика и число заказываемых предметов) —между Salesperson и Order Detail Form
   * Save the order (Сохранить заказ) —между Salesperson и Order Detail Form&#x20;
   * Create new, blank order (Создать пустой заказ) —между Order Detail Form и Order N1234
   * Set the order number, customer, order items (Ввести номер заказа, заказчика и число заказываемых предметов) —между Order Detail Form и Order N1234
   * Save the order (Сохранить заказ) —между Order Detail Form и Order N1234&#x20;

Теперь нужно поместить на диаграмму дополнительные элементы, а также рассмотреть ответственности объектов.

### Добавление на диаграмму дополнительных объектов

1. Нажмите кнопку Life Line панели инструментов.
2. Щелкните мышью где-нибудь на диаграмме, чтобы поместить туда новый объект.
3. Введите имя объекта — Order Manager (Управляющий заказами).
4. На панели инструментов нажмите кнопку Object.
5. Поместите на диаграмму еще один объект.
6. Введите его имя — Transaction Manager (Управляющий транзакциями).

### Назначение ответственностей объектам

1. Выделите сообщение 5: [Create new, blank order](#user-content-fn-19)[^19]. Выделяйте слова, а не стрелку.
2. Удалите это сообщение.
3. Повторите шаги 1 и 2 для удаления сообщений 6 и 7:
   * &#x20;Set the order number, customer, order items
   * Save the order
4. Выделите связь между объектами Order Detail Form и Order N1234.
5. Удалите эту связь.
6. На панели инструментов нажмите кнопку Connector.
7. Нарисуйте связь между Order Detail Form и Order Manager.
8. На панели инструментов нажмите кнопку Connector .
9. Нарисуйте связь между Order Manager и Order N1234.
10. На панели инструментов нажмите кнопку Connector .
11. Нарисуйте связь между Order N1234 и Transaction Manager.
12. На панели инструментов нажмите кнопку Connector .
13. Нарисуйте связь между Order Manager и Transaction Manager.
14. На панели инструментов нажмите кнопку Forward Message.
15. Щелкните мышью на связи между объектами Order Detail Form и Order Manager, чтобы ввести новое сообщение.
16. Назовите это сообщение [Save the order](#user-content-fn-20)[^20].
17. Повторите шаги 14 —16, добавив сообщения с шестого по девятое, и назвав их:&#x20;
    * [Create new, blank order](#user-content-fn-21)[^21] — между Order Manager и Order N1234&#x20;
    * [Set the order number, customer, order items](#user-content-fn-22)[^22] — между Order Manager и Order N1234
    * [Save the order](#user-content-fn-23)[^23] — между Order Manager и Transaction Manager
    * [Collect order information](#user-content-fn-24)[^24] — между Transaction Manager и Order N1234
18. На панели инструментов нажмите кнопку [Link to Self](#user-content-fn-25)[^25].
19. Щелкнув на объекте Transaction Manager, добавьте к нему рефлексивное сообщение.
20. На панели инструментов нажмите кнопку [Link Message](#user-content-fn-26)[^26].
21. Щелкните мышью на рефлексивной связи Transaction Manager, чтобы ввести туда сообщение.&#x20;
22. Назовите новое сообщение [Save the order information to the database](#user-content-fn-27)[^27].

### Соотнесение объектов с классами

1. Два раза кликните по объекту Order Options Form
2. В появившихся пиктограммах найдите кнопку Select Type, а затем выберите тип OrderOptions
3. Повторите шаги 1 и 2, соотнеся остальные объекты и соответствующие им классы:&#x20;
   * Класс OrderDetail соотнесите с объектом Order Detail Form
   * Класс OrderMgr —с объектом Order Manager&#x20;
   * Класс Order —с объектом Order N1234
   * Класс TransactionMgr —с объектом Transaction Manager

### Соотнесение сообщений с операциями

1. Два раза кликните на сообщении 1: [Create new order](#user-content-fn-28)[^28].
2. &#x20;В появившихся пиктограммах найдите кнопку Select Operation
3. В списке имен укажите имя операции —Create() .
4. Нажмите на кнопку ОК.
5. Повторите шаги 1—4 для соотнесения с операциями остальных сообщений:&#x20;
   * Сообщение 2: [Open form](#user-content-fn-29)[^29] соотнесите с операцией Open()
   * Сообщение 3: [Enter order number, customer, order items](#user-content-fn-30)[^30] — с операцией Submitlnfo()
   * Сообщение 4: [Save the order](#user-content-fn-31)[^31] — с операцией Save()
   * Сообщение 5: [Save the order](#user-content-fn-32)[^32] — с операцией SaveOrder()
   * Сообщение 6: [Create new, blank order](#user-content-fn-33)[^33] — с операцией Create()
   * Сообщение 7: [Set the order number, customer, order items](#user-content-fn-34)[^34] — с операцией Setlnfo()
   * Сообщение 8: [Save the order](#user-content-fn-35)[^35] — с операцией Save0rder()
   * Сообщение 9: [Collect order information](#user-content-fn-36)[^36] — с операцией Getlnfo()
   * Сообщение 10: [Save the order information to the database](#user-content-fn-37)[^37] — с операцией Commit()

[^1]: Life Line

[^2]: Продавец

[^3]: Выбор варианта заказа

[^4]: Создать новый заказ

[^5]: Открыть форму

[^6]: Детальная форма заказа

[^7]: Ввести номер заказа, заказчика и число заказываемых предметов

[^8]: Сохранить заказ

[^9]: Создать пустой заказ

[^10]: Сохранить заказ

[^11]: Управляющий заказами

[^12]: Управляющий транзакциями

[^13]: Создать пустой заказ

[^14]: Сохранить заказ

[^15]: Создать новый заказ

[^16]: Вести номер заказа, заказчика и число заказываемых предметов

[^17]: Сохранить заказ

[^18]: Информация о заказе

[^19]: Создать пустой заказ

[^20]: Сохранить заказ

[^21]: Создать новый заказ

[^22]: Ввести номер заказа, заказчика и число заказываемых предметов

[^23]: Сохранить заказ

[^24]: Информация о заказе

[^25]: Связь с собой

[^26]: Сообщение связи

[^27]: Сохранить информацию о заказе в базе данных

[^28]: Создать новый заказ

[^29]: Открыть форму

[^30]: Ввести номер заказа, заказчика и число заказываемых предметов

[^31]: Сохранить заказ

[^32]: Сохранить заказ

[^33]: Создать пустой заказ

[^34]: Ввести номер заказа, заказчика и число заказываемых предметов

[^35]: Сохранить заказ

[^36]: Информация о заказе

[^37]: Сохранить информацию о заказе в базе данных
