---
title: "Практическое руководство: создание Atom веб-канал закрытую галерею | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Веб-канал Atom, частные коллекции VSIX"
  - "Частные коллекции VSIX, веб-канала Atom"
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Практическое руководство: создание Atom веб-канал закрытую галерею
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно создать Atom \(RSS,\) на расположение в интрасети, содержащий расширения и добавить веб\-канал для **расширения и обновления** как частной коллекции. Для получения дополнительной информации см. [Частные коллекции](../extensibility/private-galleries.md).  
  
## Создание Atom\-канал  
 Создание канала Atom как частную коллекцию, сначала собрать расширения \(VSIX\-файлы\) в папку. Если требуется, можно объединить их в вложенные папки. Необходимо использовать следующие ресурсы:  
  
-   Файл atom.xml, который делает доступными расширения качестве частной коллекции. Сведения о подключении файла atom.xml **расширения и обновления**, в разделе [Частные коллекции](../extensibility/private-galleries.md).  
  
-   Папка, содержащая все файлы изображений, извлеченные из расширений \(например, снимки экрана\). Файл atom.xml содержит относительные ссылки на эти изображения, чтобы они были доступны в **расширения и обновления**.  
  
 Например предположим, что следующие два расширения собраны в папку:  
  
-   Template\_Wizard\_239.VSIX является пустой шаблон проекта VSIX.  
  
-   SelectionHighlight.vsix — это средство для выделения всех экземпляров выделенного слова.  
  
 Содержимое файла atom.xml будет иметь следующий вид:  
  
```  
  <?xml version="1.0" encoding="utf-8" ?> - <feed xmlns="http://www.w3.org/2005/Atom"> <title type="text" /> <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id> <updated>2011-04-14T21:25:48Z</updated> - <entry> <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id> <title type="text">Highlight all occurrences of selected word</title> <summary type="text">This extends the editor to highlight ….</summary> <published>2011-04-14T14:24:51-07:00</published> <updated>2011-04-14T14:24:22-07:00</updated> - <author> <name>Microsoft</name> </author> <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" /> <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" /> <content type="application/octet-stream" src="SelectionHighlight.vsix" /> - <Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010"> <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id> <Version>1.31</Version> <References /> <Rating xsi:nil="true" /> <RatingCount xsi:nil="true" /> <DownloadCount xsi:nil="true" /> </Vsix> </entry> - <entry> <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id> … </entry> </feed>  
  
```  
  
 Обратите внимание, что две ссылки тегов см. снимки экрана в папке созданного изображений.  
  
## См. также  
 [Частные коллекции](../extensibility/private-galleries.md)