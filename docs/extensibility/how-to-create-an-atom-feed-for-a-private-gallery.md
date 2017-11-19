---
title: "Как: создание Atom веб-канала для закрытой коллекции | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b41cb3012b937ac5448b129657064cca68a5d725
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Как: создание Atom веб-канала для закрытой коллекции
Можно создать канал Atom (RSS) в расположение в интрасети, содержащий расширения и добавить веб-канал для **расширения и обновления** качестве частной коллекции. Дополнительные сведения см. в разделе [закрытые галереи](../extensibility/private-galleries.md).  
  
## <a name="creating-an-atom-feed"></a>Создание Atom веб-канала.  
 Чтобы создать канал в качестве частной коллекции Atom, сначала сбора расширений (VSIX-файлы) в папку. Если требуется, можно объединить их в вложенные папки. Необходимо также следующие ресурсы:  
  
-   Atom.xml файл, который делает доступными расширения качестве частной коллекции. Сведения о подключении файла atom.xml **расширения и обновления**, в разделе [закрытые галереи](../extensibility/private-galleries.md).  
  
-   Папка, содержащая все файлы изображений, которые были извлечены из расширения (например, снимков экрана). Файл atom.xml содержит относительные ссылки на эти изображения, чтобы они были доступны в **расширения и обновления**.  
  
 Например предположим, что собрали следующие два расширения в папку:  
  
-   Template_Wizard_239.VSIX — пустой шаблон проекта VSIX.  
  
-   SelectionHighlight.vsix — это средство, чтобы выделить все вхождения выделенного слова.  
  
 Содержимое файла atom.xml будет выглядеть примерно так:  
  
```  
  <?xml version="1.0" encoding="utf-8" ?>   
- <feed xmlns="http://www.w3.org/2005/Atom">  
  <title type="text" />   
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
  <updated>2011-04-14T21:25:48Z</updated>   
- <entry>  
  <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
  <title type="text">Highlight all occurrences of selected word</title>   
  <summary type="text">This extends the editor to highlight ....</summary>   
  <published>2011-04-14T14:24:51-07:00</published>   
  <updated>2011-04-14T14:24:22-07:00</updated>   
- <author>  
  <name>Microsoft</name>   
  </author>  
  <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />   
  <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />   
  <content type="application/octet-stream" src="SelectionHighlight.vsix" />   
- <Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010">  
  <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>   
  <Version>1.31</Version>   
  <References />   
  <Rating xsi:nil="true" />   
  <RatingCount xsi:nil="true" />   
  <DownloadCount xsi:nil="true" />   
  </Vsix>  
  </entry>  
- <entry>  
  <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>   
  ...  
  </entry>  
  </feed>  
  
```  
  
 Обратите внимание, что два теги ссылок см. снимки экрана в папке созданный изображений.  
  
## <a name="see-also"></a>См. также  
 [Частные коллекции](../extensibility/private-galleries.md)