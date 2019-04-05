---
title: Практическое руководство. Создание Atom веб-канала для закрытой коллекции | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6d4ba78028774e8fbf8e281afa2855781dab43a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993621"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Практическое руководство. Создание веб-канала Atom для частной коллекции
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно создать Atom RSS-канал в расположение в интрасети, содержащий расширения и добавить веб-канале, **расширения и обновления** качестве частной коллекции. Дополнительные сведения см. в разделе [Закрытые коллекции](../extensibility/private-galleries.md).  
  
## <a name="creating-an-atom-feed"></a>Создание Atom веб-канала  
 Чтобы создать канал в качестве частной коллекции Atom, сначала Соберите расширений (VSIX-файлы) в папку. Если вы хотите, чтобы можно упорядочить их по вложенным папкам. Необходимо также следующие ресурсы:  
  
- Atom.xml файл, который делает доступными расширения качестве частной коллекции. Сведения о том, как подключить файл atom.xml для **расширения и обновления**, см. в разделе [частные коллекции](../extensibility/private-galleries.md).  
  
- Папку, содержащую все файлы изображений, которые были извлечены из расширений (например, снимки экрана). Файл atom.xml содержит относительных ссылок на эти образы, чтобы они были доступны в **расширения и обновления**.  
  
  Например предположим, что следующие два модуля, собранными в папку:  
  
- Template_Wizard_239.VSIX является пустой шаблон проекта VSIX.  
  
- SelectionHighlight.vsix, который представляет собой средство, чтобы выделить все экземпляры отдельного слова.  
  
  Содержимое файла atom.xml будет выглядеть следующим образом:  
  
```  
  <?xml version="1.0" encoding="utf-8" ?>   
- <feed xmlns="http://www.w3.org/2005/Atom">  
  <title type="text" />   
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
  <updated>2011-04-14T21:25:48Z</updated>   
- <entry>  
  <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
  <title type="text">Highlight all occurrences of selected word</title>   
  <summary type="text">This extends the editor to highlight ….</summary>   
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
  …  
  </entry>  
  </feed>  
  
```  
  
 Обратите внимание на то, что теги двух ссылок ссылаются на снимки экрана в папке созданного образов.  
  
## <a name="see-also"></a>См. также  
 [Частные коллекции](../extensibility/private-galleries.md)
