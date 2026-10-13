# PYVNA BORODA — автоматичний звіт Bolt Food UA

Пакет для автооновлюваного звіту партнера **PYVNA BORODA**.
Побудований за зразком інших партнерських звітів (вкладки Monthly + Weekly + Активність локацій + Невдалі замовлення, блок «Активація мережі»).

## Параметри звіту

| Параметр | Значення |
|----------|----------|
| `PARTNER_NAME` (group_name у Databricks) | `PYVNA BORODA` (52 заклади) |
| `PARTNER_DISPLAY` (заголовок) | `PYVNA BORODA` |
| `DATA_START` | `2025-01-01` |
| Initials (лого) | `PB` |
| Slug публічного репо / Pages | `pyvna-boroda-report` |
| Live URL | https://khrystynaberezna-lgtm.github.io/pyvna-boroda-report/ |
| Дані | Unity Catalog `main.ng_delivery` (UA) |

## Файли

```
PYVNA BORODA/
├── generate_report.py                 # тягне дані з Databricks → index.html
├── template.html                      # HTML-шаблон (брендинг Bolt, Chart.js)
├── publish.sh                         # генерація + git push у публічний репо
├── requirements.txt                   # databricks-sql-connector
├── .env                               # конфіг + Databricks PAT (НЕ в git)
├── .env.example                       # шаблон конфігу
├── .gitignore                         # .env та report_data.json не комітяться
├── cursor-rule.mdc                    # правило Cursor для цього звіту
├── README.md                          # цей файл
└── .github/workflows/update-report.yml  # автооновлення щопонеділка (05:00/07:00/09:00 UTC)
```

## Оновлення

- **Автоматично**: GitHub Actions щопонеділка (резервні запуски 05:00 / 07:00 / 09:00 UTC).
- **Вручну**: репо → Actions → «Оновлення звіту PYVNA BORODA» → Run workflow.
- **Локально**: `cd "PYVNA BORODA" && ./publish.sh`.

> Databricks PAT живе 90 днів — після прострочення згенеруй новий і онови `.env`
> та секрет `DATABRICKS_TOKEN` у репо.
