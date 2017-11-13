# laravel-flysystem-azure

Laravel Azure blob storage service provider

> Only for **blob storage**!

## Usage

- Register service provider in `config/app.php`.

```php
'providers' => [
    AzureStorageServiceProvider::class,
]
```

- Register disk in `config/filesystem.php`.

```php
'disks' => [
    'azure'  => [
        'driver'    => 'azure',
        'account'   => [
            'name' => env('AZURE_ACCOUNT_NAME'),
            'key'  => env('AZURE_ACCOUNT_KEY'),
        ],
        'blob-endpoint'  => env('AZURE_BLOB_ENDPOINT'),
        'container' => 'my-container'
    ]
]
```

You can register multiple azure containers with different disk names:

```php
'disks' => [
    'azure-reports'  => [
        'driver'    => 'azure',
        'account'   => [
            'name' => env('AZURE_ACCOUNT_NAME'),
            'key'  => env('AZURE_ACCOUNT_KEY'),
        ],
        'blob-endpoint'  => env('AZURE_BLOB_ENDPOINT'),
        'container' => 'reports'
    ],
    
    'azure-images'  => [
        'driver'    => 'azure',
        'account'   => [
            'name' => env('AZURE_ACCOUNT_NAME'),
            'key'  => env('AZURE_ACCOUNT_KEY'),
        ],
        'blob-endpoint'  => env('AZURE_BLOB_ENDPOINT'),
        'container' => 'images'
    ]
]
```

- Set azure account and key.

- Use `Storage::disk('azure')->get()`.