---
title: Welcome to Evidence
---

How does Evidence Work? I don't care!

This demo [connects](/settings) to a local DuckDB file `needful_things.duckdb`.

<LineChart
  data={orders_by_month}
  x=order_mo
  y=sales
  yFmt=usd0k
  title = "Sales by Month, USD"
  sort = false
/>

## Write in Markdown

Evidence renders markdown files into web pages. This page is:
`[project]/pages/index.md`.

## Run SQL using Code Fences

```sql orders_by_month
select
  substr(order_datetime,0,8) as order_mo,
  count(*) as number_of_orders,
  sum(sales) as sales,
  sum(sales)/count(*) as average_order_value
from orders
where order_datetime >= '2020-01-01'
group by 1 
order by 1
```

In your markdown file, you can include SQL queries in code fences. Evidence will run these queries through your database and return the results to the page.

<Alert status=info>  
To see the queries on a page, click the 3-dot menu at the top right of the page and Show Queries. You can see both the SQL and the query results by interacting with the query above.
</Alert>

## Visualize Data with Components

### Value in Text

Last month customers placed **<Value data={orders_by_month} column=number_of_orders/>** orders. The AOV was **<Value data={orders_by_month} column=average_order_value fmt=usd2/>**.

### Big Value 
<BigValue data={orders_by_month} value=sales fmt=usd0/>
<BigValue data={orders_by_month} value=number_of_orders />


### Bar Chart

<BarChart 
  data={orders_by_month} 
  y=number_of_orders 
  fillColor="#488f96"
  sort=false
/>

> **Try:** Change the chart to a `<LineChart>`.

### Data Table

<DataTable data={orders_by_month} rows=6/>

> **More:** See [all components](https://docs.evidence.dev/components/all-components)

# Share with Evidence Cloud

Evidence Cloud is the easiest way to securely share your project. 
- Get your project online
- Authenticate users
- Schedule data refreshes

  <BigLink href='https://du3tapwtcbi.typeform.com/waitlist?utm_source=cloud-page&typeform-source=evidence.dev'>Deploy to Evidence Cloud &rarr;</BigLink>

You can use Netlify, Vercel or another static hosting provider to [self-host Evidence](https://docs.evidence.dev/deployment/overview).

# Get Support

- Message us on [Slack](https://slack.evidence.dev/)
- Read the [Docs](https://docs.evidence.dev/)
- Open an issue on [Github](https://github.com/evidence-dev/evidence)
