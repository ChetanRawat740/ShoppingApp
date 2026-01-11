# Entity Relationship Diagram (ERD)

## Overview
This ERD represents the main entities in the ShoppingApp based on the database.json structure.

## Entities

### Banner
- **Attributes:**
  - url (String): URL of the banner image

### Category
- **Attributes:**
  - id (Integer): Unique identifier for the category
  - picUrl (String): URL of the category image
  - title (String): Name of the category (e.g., "Adidas", "Nike")

### Items
- **Attributes:**
  - title (String): Name of the item
  - description (String): Description of the item
  - picUrl (Array of Strings): URLs of item images
  - price (Float): Price of the item
  - rating (Float): Rating of the item
  - size (Array of Strings): Available sizes for the item

## Relationships

```
+----------------+       +-----------------+
|     Banner     |       |    Category     |
+----------------+       +-----------------+
| - url          |       | - id            |
+----------------+       | - picUrl        |
                         | - title         |
                         +-----------------+
                                 |
                                 | 1:N (optional)
                                 |
                         +-----------------+
                         |      Items      |
                         +-----------------+
                         | - title         |
                         | - description   |
                         | - picUrl[]      |
                         | - price         |
                         | - rating        |
                         | - size[]        |
                         +-----------------+
```

### Relationship Details
- **Category to Items**: One category can have multiple items (1:N). However, based on the current data structure, items do not have a direct foreign key to categories. This relationship is inferred from the category titles and item titles, but not explicitly defined in the JSON.

### Notes
- The app uses TinyDB (SharedPreferences wrapper) for local data storage.
- Images are stored remotely (Firebase Storage) and referenced by URLs.
- Cart management is handled by ManagmentCart class (not shown in ERD as it's runtime data).
