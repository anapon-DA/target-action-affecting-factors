# Выявление и анализ факторов, влияющих на выполнение целевого действия пользователями мобильного приложения по продаже вещей

[Ссылка на проект](https://nbviewer.org/github/anapon-DA/projects/blob/main/Identifying%20Factors%20for%20a%20Target%20Action%20%28Mobile%20App%29/sales-app.ipynb) :point_left:

[Ссылка на презентацию](https://disk.yandex.ru/i/JqD-tdpB4FnvUg) :woman_teacher:

[Ссылка на дашборд (Tableau)](https://public.tableau.com/app/profile/anastasiia5402/viz/MobileAppDashboard_16573926438810/MobileAppDashboard) :bar_chart:

На основе данных о действиях пользователей мобильного приложения (приложение для продажи вещей) необходимо проанализировать связь целевого события — просмотра контактов — и других действий пользователей, а также оценить, какие действия чаще совершают те пользователи, которые просматривают контакты.

Предоставлены данные о событиях, совершенных в мобильном приложении:

- датасет с данными об источниках скачивания приложения: 

	- `userId` — идентификатор пользователя
	- `source` — источник, из которого пользователь установил приложение

- журнал событий:
	- `event.time` — время совершения действия
	- `user.id` — идентификатор пользователя
	- `event.name` — действие пользователя

| [Рендер проекта на `nbviewer`](https://nbviewer.org/github/anapon-DA/projects/blob/main/Identifying%20Factors%20for%20a%20Target%20Action%20%28Mobile%20App%29/sales-app.ipynb) | [Проект на `github`](https://github.com/anapon-DA/projects/blob/main/Identifying%20Factors%20for%20a%20Target%20Action%20(Mobile%20App)/sales-app.ipynb) |
| --- | --- |
| **корректный переход по внутренним ссылкам в оглавлении проекта, отображаются интерактивные графические объекты Plotly** | статичный вариант |

# Выводы

Основные пути, по которым пользователи доходят до выполнения целевого действия `contacts_show` - это действия search, map и tips_click. Самая "быстрая" из воронок - это воронка с map: медиана времени, прошедшего от map до contacts_show составила 57.8 секунд для всех целевых действий и 52.9 секунд для первого выполнения целевого действия пользователем. Таким образом, пользователи часто выбирают объявление, исходя из удобного для них района (действие `map` - просмотр карты объявлений). Самая "медленная" конверсия - у tips_click (медиана - более 11 минут для всех действий и более 6 минут для первых просмотров контактов). 

Пользователи, которые просматривали контакты, чаще видели рекомендованные объявления (событие `tips_show`), кликали на них (действие `tips_click`), а также просматривали карту объявлений (действие `map`). Это подтверждают корреляционные связи средней силы, которые выявлены между этими действиями и целевым действием `contacts_show`. Также пользователи, просматривавшие контакты, чаще открывали карточки объявлений `advert_open`.

Когортный анализ демонстрирует уверенный прирост конверсии в целевое действие `contacts_show` внутри каждой когорты (горизонт анализа 7 дней), а конверсия в просмотры контактов на 7-й день жизни у когорт пользователей, зарегистрировавшихся 7 октября и 28 октября, не различаются: показатель конверсии стабилен.

Существуют статистически значимые различия в конверсии в просмотры контактов для группы пользователей, которые видели рекомендованные объявления, но не взаимодействовали с ними (не совершали действие `tips_click`), и группы пользователей, которые видели и кликали на них (совершали действие `tips_click`): для пользователей, **не** совершавших `tips_click`, конверсия составила 17%, тогда как для **совершавшей** `tips_click` группы - 30.6% (уровень значимости 0.025).


**Рекомендации**

В целях повышения конверсии в просмотр контактов рекомендуется:
- предлагать рекомендованные объявления (tips_show), исходя из геолокации пользователя;
- рекомендовать пользователям воспользоваться картой объявлений;
- добавить показ рекомендованных объявлений в поисковой выдаче и на карте объявлений;
- увеличить частоту показа рекомендованных объявлений для пользователей, не просматривавших контакты;
- рассмотреть возможность редизайна рекомендованных объявлений в целях повышения конверсии из `tips_show` в `tips_click`;
- изучить перспективы улучшения алгоритма поиска в приложении.

# Статус проекта

:white_check_mark: Завершен

# Инструменты

`Matplotlib`
`Pandas`
`Plotly`
`Python`
`Scikit-learn`
`Seaborn`
