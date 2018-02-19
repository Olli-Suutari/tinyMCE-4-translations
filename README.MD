This repository includes the translation files for the TinyMCE 4 WYSIWYG text editor, published as a Github page. The translations were downloaded from here: https://www.tinymce.com/download/language-packages/  on 16/01/2018. The Finnish translation was missing and was downloaded from here instead: http://archive.tinymce.com/i18n/

To use the translations, just place the correct url to the TinyMCE configuration, you probably want to set a matching language as well.    (Example for [react-tinymce](https://github.com/instructure-react/react-tinymce) )

                        <TinyMCE
                            config={{
                                language_url: 'https://olli-suutari.github.io/tinyMCE-4-translations/fi.js',
                                language: 'fi',
                            }}
                        />

This is especially useful if using local translation files is not possible.

Note: The TinyMCE offical Git repository can be found from here:

https://github.com/tinymce/tinymce

It is also possible to set the language url to a variable and change it as the user changes the language, note that the language should be defined as well. Example code for react could look a bit like this:
    
    import React, { Component } from 'react';
    import PropTypes from 'prop-types';
    import { connect } from 'react-redux';
    import { injectIntl, intlShape, FormattedMessage } from 'react-intl';
    // Reactstrap: https://reactstrap.github.io/
    import { Button, Form, FormGroup, Label, Input, Modal, ModalHeader, ModalBody, ModalFooter } from 'reactstrap';
    import TinyMCE from 'react-tinymce';
 
    export class Example extends Component {
    
    constructor(props) {
        super(props);
        this.state = {
            tinyMCELang: 'https://olli-suutari.github.io/tinyMCE-4-translations/fi.js',
            tinyMCELocale: 'fi'
        };
    }
    componentWillReceiveProps(nextProps) {
        // Change TinyMCE language
        // See: https://github.com/Olli-Suutari/tinyMCE-4-translations
        if(nextProps.intl.locale !== this.props.intl.locale)
        {
            if(nextProps.intl.locale === 'en')
            {
                this.setState({
                    tinyMCELang: 'https://olli-suutari.github.io/tinyMCE-4-translations/en_GB.js',
                    tinyMCELocale: 'en_GB',
                });
            }
            else if(nextProps.intl.locale === 'fi')
            {
                this.setState({
                    tinyMCELang: 'https://olli-suutari.github.io/tinyMCE-4-translations/fi.js',
                    tinyMCELocale: 'fi',
                });
            }
        }
    }
    
    render() {
        let langUrl = this.state.tinyMCELang;
        let locale = this.state.tinyMCELocale;
        return (
    			...
                <FormGroup>
                  <Label>Members</Label>
                    <TinyMCE
                        id={'members'}
                        content={this.state.members}
                        config={{
                            language_url: langUrl,
                            language: locale,
                        }}
                    />
                </FormGroup>
    			...
        );
      }
    }


