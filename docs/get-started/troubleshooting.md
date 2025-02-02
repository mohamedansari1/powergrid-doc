# Troubleshooting

This section covers the most frequent issues that users may encounter while using PowerGrid.

Here you will find:

[[toc]]

## Multiple instances of Alpine

If you are installing PowerGrid with Laravel Breeze, you may come across this particular issue.

Please refer to Livewire Documentation [Multiple instances of Alpine](https://livewire.laravel.com/docs/troubleshooting#multiple-instances-of-alpine).

## Undefined variable "$foobar"

Please refer to [Theme, layout, view and "variable undefined" errors](/get-started/troubleshooting.html#theme-layout-view-and-variable-undefined-errors).

## Call to undefined method "fooBar()"

Please check the [Upgrade Guide](/release-notes-and-upgrade/upgrade-guide.html).

Additionally, you may also learn the section [Theme, layout, view and "variable undefined" errors](/get-started/troubleshooting.html#theme-layout-view-and-variable-undefined-errors).

## Theme, layout, view and "variable undefined" errors

Most likely you have published the PowerGrid views, and they have become outdated. This can happen after updating PowerGrid while using customized views.

To solve this problem, first back up your PowerGrid resource: Copy the `resources/views/vendor/livewire-powergrid` directory to `resources/views/vendor/livewire-powergrid-BACKUP`.

Then, proceed to republish your views. Run the command below.

```shell
php artisan vendor:publish --tag=livewire-powergrid-views
```

Next, clear Laravel caches. Run the command below.

```shell
php artisan optimize:clear
```

## Failed to mount filter: Filter::datetime

You must install Flatpickr. Please refer to the section [Plugins Configuration >
Flatpickr](/get-started/powergrid-configuration.html#flatpickr).

## Flatpickr Locale Support

Sometimes Flatpickr will not support your location's locale setting.

For example, consider that your application is configured for `pt_BR` in `config/app.php` with `'locale' => 'pt_BR'`,

In the file `config/livewire-powergrid.php`, you might have tried to add the same locale `pt_BR`.
 the same string for locale.  

However, Flatpick doesn't accept `pt_BR`. Instead, change it to `pt`.

```php{7}
     'plugins' => [
        // ...
        'flatpickr' => [
            // ...
            'locales'   => [
                'pt_BR' => [
                    'locale'     => 'pt_BR', // [!code --]
                    'locale'     => 'pt', // [!code ++]
                    'dateFormat' => 'd/m/Y H:i',
                    'enableTime' => true,
                    'time_24hr'  => true,
                ],
            ],
        ],
    ],
```

---
