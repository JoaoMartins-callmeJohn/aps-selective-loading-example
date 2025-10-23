# APS Viewer Selective Loading Example

A sample application demonstrating how to selectively load elements in the Autodesk Platform Services (APS) Viewer based on property filtering. This example shows how to improve performance and user experience by loading only specific model elements that match certain criteria.

## Overview

This sample showcases the selective loading capabilities of the APS Viewer v7, allowing users to filter and load only specific elements from a model based on their properties. This is particularly useful for large models where loading everything at once might impact performance.

## Live Demo

LIVE DEMO CURRENTLY POINTS TO AGGREGATED BRANCH AS A TEST.
You can test this sample live here: https://joaomartins-callmejohn.github.io/aps-selective-loading-example/

## How It Works

The selective loading uses the APS Viewer's `property_query` filter with the following structure:

```javascript
viewer.loadDocumentNode(doc, viewables, {
  filter: {
    property_query: {
      "$or": [
        { "$like": ["?PropertyName", "'%Value1%'"] },
        { "$like": ["?PropertyName", "'%Value2%'"] }
      ]
    }
  }
});
```

### Key Components:

- **Property Lookup Syntax**: Uses `?PropertyName` to query by property name
- **$like Operator**: Performs partial matching with wildcards (`%`)
- **$or Operator**: Combines multiple conditions with OR logic
- **Quoted Values**: Values are wrapped in single quotes for the query

## API Reference

This sample uses the following APS Viewer APIs:

- [`Autodesk.Viewing.Document.load()`](https://aps.autodesk.com/en/docs/viewer/v7/reference/Viewing/Document/#load-documentid-onsuccesscallback-onerrorcallback-accesscontrolproperties)
- [`viewer.loadDocumentNode()`](https://aps.autodesk.com/en/docs/viewer/v7/reference/Viewing/GuiViewer3D/#loaddocumentnode-avdocument-manifestnode-options)
- [Selective Loading Documentation](https://aps.autodesk.com/en/docs/viewer/v7/developers_guide/advanced_options/selective-loading/)

## License

This sample is licensed under the terms of the [MIT License](LICENSE). Please see the [LICENSE](LICENSE) file for full details.
