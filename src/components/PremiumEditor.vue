<template>
    <ckeditor :editor="ClassicEditor" v-model="editorData" :config="editorConfig"></ckeditor>
</template>

<script setup>
import { ref } from 'vue'
import { ClassicEditor } from '@ckeditor/ckeditor5-editor-classic';
// Premium
import { MultiLevelList } from '@ckeditor/ckeditor5-list-multi-level';
import { ExportPdf } from '@ckeditor/ckeditor5-export-pdf';
import { ExportWord } from '@ckeditor/ckeditor5-export-word';
import { RealTimeCollaborativeEditing } from '@ckeditor/ckeditor5-real-time-collaboration';
import { CKBox, CKBoxImageEdit } from "@ckeditor/ckeditor5-ckbox";
// Default

import { Alignment } from '@ckeditor/ckeditor5-alignment';  // Importing the package.
import { Autoformat } from '@ckeditor/ckeditor5-autoformat';
import { Bold, Italic } from '@ckeditor/ckeditor5-basic-styles';
import { BlockQuote } from '@ckeditor/ckeditor5-block-quote';
import { CloudServices } from '@ckeditor/ckeditor5-cloud-services';
import { Essentials } from '@ckeditor/ckeditor5-essentials';
import { Heading } from '@ckeditor/ckeditor5-heading';
import {
    Image,
    ImageCaption,
    ImageStyle,
    ImageToolbar,
    ImageUpload,
    PictureEditing
} from '@ckeditor/ckeditor5-image';
import { Indent } from '@ckeditor/ckeditor5-indent';
import { Link } from '@ckeditor/ckeditor5-link';
import { List } from '@ckeditor/ckeditor5-list';
import { MediaEmbed } from '@ckeditor/ckeditor5-media-embed';
import { Paragraph } from '@ckeditor/ckeditor5-paragraph';
import { PasteFromOffice } from '@ckeditor/ckeditor5-paste-from-office';
import { Table, TableToolbar } from '@ckeditor/ckeditor5-table';
import { TextTransformation } from '@ckeditor/ckeditor5-typing';
import { Comments } from '@ckeditor/ckeditor5-comments';
import { AIAssistant, OpenAITextAdapter } from '@ckeditor/ckeditor5-ai';

const editorData = ref('This is the default value.')
const editorConfig = {
    plugins: [
        // Premium
        OpenAITextAdapter,
        AIAssistant,
        MultiLevelList,
        ExportPdf,
        ExportWord,
        RealTimeCollaborativeEditing,
        Comments,
        CKBox,
        CKBoxImageEdit,
        // Default
        List,
        PictureEditing,
        Alignment,  // Adding the package to the list of plugins.
        Autoformat,
        BlockQuote,
        Bold,
        CloudServices,
        Essentials,
        Heading,
        Image,
        ImageCaption,
        ImageStyle,
        ImageToolbar,
        ImageUpload,
        Indent,
        Italic,
        Link,
        MediaEmbed,
        Paragraph,
        PasteFromOffice,
        Table,
        TableToolbar,
        TextTransformation
    ],
    toolbar: [
        'aiAssistant',
        'exportPdf',
        'multiLevelList',
        'exportWord',
        'comment',
        'ckbox', 'ckboxImageEdit',
        '|',
        'alignment',  // Displaying the proper UI element in the toolbar.
        'heading',
        '|',
        'bold',
        'italic',
        'link',
        'bulletedList',
        'numberedList',
        '|',
        'outdent',
        'indent',
        '|',
        'imageUpload',
        'blockQuote',
        'insertTable',
        'mediaEmbed',
        'undo',
        'redo'],
    licenseKey: '',
    cloudServices: {
        tokenUrl: '',
        webSocketUrl: '',
        uploadUrl: ''
    },
    collaboration: {
        channelId: 'document-id-test-123'
    },
    comments: {
        editorConfig: {
            // The list of plugins that will be included in the comments editors.
            extraPlugins: [Bold, Italic, List, Autoformat]
        }
    },
    ai: {
        // AI Assistant feature configuration.
        // https://ckeditor.com/docs/ckeditor5/latest/features/ai-assistant.html
        aiAssistant: {
            contentAreaCssClass: "formatted"
        },
        // Configure one of the supported AI integration: OpenAI, Azure OpenAI, Amazon Bedrock
        // https://ckeditor.com/docs/ckeditor5/latest/features/ai-assistant/ai-assistant-integration.html#integration
        openAI: {
            requestHeaders: {
                Authorization: 'Bearer'
            }
        }
    },
}

</script>

<style>
body {
    color: #000;
}

.ck.ck-editor__editable_inline:not(.ck-editor__nested-editable) {
    min-height: 400px;
}

/* Styles to render an editor with a sidebar for comments & suggestions */
.container {
    display: flex;
    flex-direction: row;
}
</style>