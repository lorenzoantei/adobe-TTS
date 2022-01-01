---
title: "Rand colors"
date: 2021-12-31 12:40:00 +0100

categories: ["Adobe Illustrator"]
description: "Replace background of filled shapes with random colors"
thumbnail: "https://i.stack.imgur.com/nbCNE.png"
image: "https://i.stack.imgur.com/nbCNE.png"

layout: post
---

<a href="../../assets/js/catalogue/ai__random-colors.js" download>Click to Download</a>

```
mySelection = app.activeDocument.selection;
myDoc = app.activeDocument;
if (mySelection instanceof Array)
{
	selSwatches = myDoc.swatches.getSelected();

	if(selSwatches.length != 0)
		for (i=0; i<mySelection.length; i++)
		{
			if(mySelection[i].typename == "PathItem" || mySelection[i].typename == "CompoundPathItem")
			{
				selItem = mySelection[i];
				selItem.filled = true;

				swatchIndex = Math.round( Math.random() * (selSwatches.length - 1 ));

				if(selItem.typename == "PathItem")
					selItem.fillColor = selSwatches[swatchIndex].color;
				else
					selItem.pathItems[0].fillColor = selSwatches[swatchIndex].color;

			}
		}
}
```

[fonte](https://github.com/psstmatt/Random-Swatch-Fill)
