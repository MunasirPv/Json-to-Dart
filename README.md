# JSON to Dart

Speed up your Flutter development by instantly generating Dart data models from JSON objects.

## Features

- **Instant Conversion**: Convert any selected JSON text into a Dart class.
- **Auto-Generation**: Automatically generates:
  - Class properties with types.
  - Constructor with `required` named parameters.
  - `fromJson` factory method for parsing.
  - `toJson` method for serialization.
- **Type Support**: Handles Strings, Numbers (int/double), Booleans, Attributes.

## How to Use

1.  Open a file in VS Code.
2.  Paste your JSON object or select an existing JSON block.
    ```json
    {
      "name": "Flutter",
      "version": 3.0,
      "isCool": true
    }
    ```
3.  Highlight/Select the JSON text.
4.  Open the Command Palette (`Cmd+Shift+P` / `Ctrl+Shift+P`).
5.  Run the command: **Convert Selection to Dart Model**.
6.  Enter the desired **Class Name** when prompted (e.g., `Framework`).
7.  The selected JSON will be replaced by the generated Dart code:

    ```dart
    class Framework {
      final String name;
      final double version;
      final bool isCool;
    
      Framework({
        required this.name,
        required this.version,
        required this.isCool,
      });
    
      factory Framework.fromJson(Map<String, dynamic> json) {
        return Framework(
          name: json['name'],
          version: json['version'],
          isCool: json['isCool'],
        );
      }
    
      Map<String, dynamic> toJson() {
        return {
          'name': name,
          'version': version,
          'isCool': isCool,
        };
      }
    }
    ```

## Requirements

- VS Code version 1.107.0 or higher.
- No additional dependencies required.

## Known Issues

- **Arrays**: Currently, all arrays are typed as `List<dynamic>`. Complex nested lists may require manual type adjustment.
- **Nested Objects**: Nested objects are currently typed as `Map<String, dynamic>`. You may want to generate separate classes for nested objects manually.

## Release Notes

### 0.0.1

- Initial release of JSON to Dart.
- Basic JSON parsing and Dart class generation.
