---
layout: post
title: Laravel Excel Freeze Pane
status: publish
categories: [Laravel, excel]
---

This is how you freeze a column or a row when using Laravel Excel.

```php
class User implements WithEvents
{
    public function registerEvents(): array
    {
        return AfterSheet::class => function(AfterSheet $event) {
              $event->sheet->freezePane('B1');
            },
        ];
    }
}
```

See how to freeze pane from <a href="https://github.com/PHPOffice/PhpSpreadsheet/blob/master/src/PhpSpreadsheet/Worksheet/Worksheet.php#L1992">PhpSpreadsheet/Worksheet.php</a> on GitHub.
