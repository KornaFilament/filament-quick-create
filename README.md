# Quick Create for Filament

Plugin for [Filament Admin Panel](https://filamentphp.com) that adds a dropdown menu to the header to quickly create new items from anywhere in your app.

![quick-create-og](https://github.com/awcodes/filament-quick-create/assets/3596800/ae05db80-b3e2-4c12-938b-d4339844d481)

## Installation

Install the package via composer

```bash
composer require awcodes/filament-quick-create
```

## Usage

By default, Quick Create will use all resources that are registered with current Filament context. All resources will follow the authorization used by Filament, meaning that if a user doesn't have permission to create a record it will not be listed in the dropdown.

### Registering the plugin

```php
use Awcodes\FilamentQuickCreate\QuickCreatePlugin;

public function panel(Panel $panel): Panel
{
    return $panel
        ->plugins([
            QuickCreatePlugin::make(),
        ])
}
```

> **Warning**
> Excludes and includes are not meant to work together. You should use one or the other, but not both.

### Excluding Resources

Excluding resources will filter them out of the registered resources to prevent them from displaying in the dropdown.

```php
use Awcodes\FilamentQuickCreate\QuickCreatePlugin;

public function panel(Panel $panel): Panel
{
    return $panel
        ->plugins([
            QuickCreatePlugin::make()
                ->excludes([
                    \App\Filament\Resources\UserResource::class,
                ]),
        ])
}
```

### Including Resources

Sometimes, it might be easier to only include some resources instead of filtering them out. For instance, you have 30 resources but only want to display 3 to 4 in the dropdown.

```php
use Awcodes\FilamentQuickCreate\QuickCreatePlugin;

public function panel(Panel $panel): Panel
{
    return $panel
        ->plugins([
            QuickCreatePlugin::make()
                ->includes([
                    \App\Filament\Resources\UserResource::class,
                ]),
        ])
}
```

### Sorting

By default, Quick Create will sort all the displayed options in descending order. This can be disabled should you choose. In which case they will be displayed in the order they are registered with Filament.

```php
use Awcodes\FilamentQuickCreate\QuickCreatePlugin;

public function panel(Panel $panel): Panel
{
    return $panel
        ->plugins([
            QuickCreatePlugin::make()
                ->sort(false),
        ])
}
```
