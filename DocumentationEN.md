
# TabularTXT (TTXT) Format Documentation v1.0

## Format Specification

### 1. File Structure
Each translation file MUST contain exactly 3 elements in strict order:
```ttxt
name = {Language Name}
iso-code = {Language Code}
language{
    {id} , {Translated Phrase};
    {id} , {Translated Phrase};
    ...
}
```

### 2. Required Elements
| Element     | Format              | Example           | Description                      |
|-------------|---------------------|-------------------|----------------------------------|
| name        | `name = value`      | `name = Russian`  | Full language name               |
| iso-code    | `iso-code = code`   | `iso-code = ru`   | ISO language code                |
| language{}  | Translation block   | (see below)       | Container for all translations   |

### 3. language{} Block
Syntax:
```ttxt
language{
    identifier , translated text;
    identifier , translated text;
    ...
}
```

Rules:
1. **Starts** with `language{` on a separate line
2. **Ends** with `}` on a separate line
3. **Each translation line** contains:
   - Phrase ID in English
   - Comma
   - Localized text
   - Trailing semicolon
4. **Last line** NO LONGER requires a semicolon

### 4. File Example
```ttxt
name = Russian
iso-code = ru
language{
    play-tab , Играть;
    news-tab , Новости;
    settings-tab , Настройки;
    launch-button , ЗАПУСТИТЬ MINECRAFT;
    about-text , Простой лаунчер Minecraft на Python и Qt;
}
```

### 5. Strict Rules
1. Element order is fixed:
   ```plaintext
   1. name
   2. iso-code
   3. language{}
   ```
2. The `language` block prohibits:
   - Empty lines
   - Comments
   - Nested blocks
3. ID case sensitivity: `Play-Tab` ≠ `play-tab`

### 6. Error Handling
The parser MUST check:
1. Presence of all 3 required elements
2. Correct structure of the language block
3. Absence of duplicate IDs in language block
4. Proper format of each translation line
```

Key translation notes:
1. Maintained RFC-style terminology (MUST/SHOULD)
2. Technical terms standardized:
   - "Локализованный текст" → "Localized text"
   - "Идентификатор" → "Identifier"
   - "Дубликаты ID" → "Duplicate IDs"
3. Imperative forms preserved ("Starts with", "Ends with")
4. Formatting and code blocks remain unchanged
5. Clarified "NO LONGER requires" for version-specific behavior
