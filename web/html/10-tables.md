# Tables

Tables display tabular data. Related: [Lists](07-lists), [Semantic](05-semantic).

## Basic Table

```html
<table>
    <tr>
        <th>Header 1</th>
        <th>Header 2</th>
    </tr>
    <tr>
        <td>Data 1</td>
        <td>Data 2</td>
    </tr>
</table>
```

## Table Elements

| Element | Description |
|---------|-------------|
| `<table>` | Table container |
| `<thead>` | Header row group |
| `<tbody>` | Body rows |
| `<tfoot>` | Footer row group |
| `<tr>` | Table row |
| `<th>` | Header cell |
| `<td>` | Data cell |

## Complete Example

```html
<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Age</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Alice</td>
            <td>30</td>
        </tr>
        <tr>
            <td>Bob</td>
            <td>25</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>Average</td>
            <td>27.5</td>
        </tr>
    </tfoot>
</table>
```

## Spanning Columns/Rows

```html
<!-- Column span -->
<td colspan="2">Spans 2 columns</td>

<!-- Row span -->
<td rowspan="3">Spans 3 rows</td>
```

## Scope Attribute

```html
<th scope="col">Column Header</th>
<th scope="row">Row Header</th>
```

## Responsive Table

```html
<div style="overflow-x:auto">
    <table>
        <!-- table content -->
    </table>
</div>
```