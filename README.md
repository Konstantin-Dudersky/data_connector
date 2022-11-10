
## Порядок работы

Перед началом смены мастер выгружает задание на производство. Задание задается в виде
- несколько подзадач:
	- тип шин
	- необходимое кол-во для производства
	- нормативное время производства одной шины данного типа ($ICT_i$).
- плановый простой (перерывы, переналадка) в минутах ($PSD_S$ - planned shut down).

Общее кол-во подзадач - ST (subtasks). Отменить задание (при ошибке или необходимости внести изменения) может только мастер.

На АРМе оператор заходит под своей учетной записью и подтверждает задание. Фиксируется время начала.

При наличии неисправностей необходимо выбрать указать причину. Суммарное время нахождения в аварийном состоянии - $DTL_S$.

По мере выполнения оператор закрывает подзадачи. При закрытии необходимо ввести кол-во хороших ($GP_i$) / бракованных шин. Общее число шин - $TP_i$.

После выполнения всех заданий оператор закрывает смену. Фиксируется время окончания.

### Формулы для расчета OEE за смену

Индекс $_S$ (shift) означает расчетные данные за смену

Обозначение $ST$ - кол-во подзадач для выполнения за одну смену.

Plant Operating Time (POT):
$$ POT_S - $$ промежуток времени между началом и окончанием смены

Planned production time (PPT):
$$ PPT_S = POT_S - PSD_S $$

Operating Time (OT):
$$ OT_S = PPT_S - DTL_S$$

Good peices (GP):
$$ GP_S = \sum_{i=1}^{ST} GP_i $$

Total pieces (TP):
$$ TP_S = \sum_{i=1}^{ST} TP_i $$

Ideal time (IT):
$$ IT_S = \sum_{i=1}^{ST} (ICT_i \times TP_i) $$

Availability (A):
$$ A_S = \frac{OT_S}{PPT_S} $$

Performance (P):
$$ P_S = \frac{IT_S}{OT_S} $$

Quality (Q):
$$ Q_S = \frac{GP_S}{TP_S} $$

Overall equipment efficiency (OEE):
$$ OEE_S = A_S \times P_S \times Q_S $$

Все данные с индексом $_S$ сохраняются в базе данных в привязке к выполненной смене.

### Формулы для расчета OEE за произвольный промежуток времени

При расчете OEE за произвольный промежуток времени определяется кол-во смен, попавших в данный диапазон времени, общее кол-во - TS (total shifts).

Plant Operating Time (POT):
$$ POT - $$ весь промежуток времени, астрономическое время

Planned production time (PPT):
$$ PPT = POT - \sum_{S=1}^{TS} PSD_S $$

Availability (A):
$$ A = \frac{ \sum_{S=1}^{TS} OT_S }{ PPT } $$

Performance (P):
$$ P = \frac{ \sum_{S=1}^{TS} IT_S }{ \sum_{S=1}^{TS} OT_S } $$

Quality (Q):
$$ Q = \frac{ \sum_{S=1}^{TS} GP_S}{ \sum_{S=1}^{TS} TP_S} $$

Overall equipment efficiency (OEE):
$$ OEE = A \times P \times Q $$

## Интерфейс

Главная страница

- Зарегестрированный пользователь. Кнопка входа / регистрации.
- Задание на смену. Кнопки запуска, паузы, окончания. После окончания - окошко с вводом кол-ва нормальных / бракованных шин.
- Перечень активных неисправностей

Управление пользователями
- добавление / удаление / редактирование пользователей

Просмотр истории

Расчет OEE по сменам

Расчет OEE за период времени




plotly timeline - https://stackoverflow.com/a/50646793