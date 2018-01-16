This repository includes the translation files for the TinyMCE 4 WYSIWYG text editor, published as a Github page. The translations were downloaded from here: https://www.tinymce.com/download/language-packages/  on 16/01/2018. The Finnish translation was missing and was downloaded from here instead: http://archive.tinymce.com/i18n/

To use the translations, just place the correct url to the TinyMCE configuration. (Example for [react-tinymce](https://www.npmjs.com/package/react-tinymce) )

```
                    <TinyMCE
                        config={{
                            language_url: 'https://olli-suutari.github.io/tinyMCE-4-translations/fi.jss',
                        }}
                    />
```

This is especially useful if using local translation files is not possible.

It is also possible to set the language url to a variable and change it as the user changes the language.

                    <TinyMCE
                        config={{
                            language_url: langUrlVariable,
                        }}
                    />


Note: The TinyMCE offical Git repository can be found from here:

https://github.com/tinymce/tinymce
