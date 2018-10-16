---
title: 'Практическое: создание Atom веб-канала для закрытой коллекции | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0ea9df0bac68f9c16f5442d04fa4229f21bb29b2
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638496"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Практическое: Создание канала для закрытой коллекции Atom
Можно создать Atom RSS-канал в расположение в интрасети, содержащий расширения и добавить веб-канале, **расширения и обновления** качестве частной коллекции. Дополнительные сведения см. в разделе [закрытые коллекции](../extensibility/private-galleries.md).  
  
## <a name="create-an-atom-feed"></a>Создать канал Atom  
 Чтобы создать канал в качестве частной коллекции Atom, сначала собрать расширений (*.vsix* файлы) в папку. Если вы хотите, чтобы можно упорядочить их по вложенным папкам. Необходимо также следующие ресурсы:  
  
-   *Atom.xml* файл, который делает доступными расширения качестве частной коллекции. Сведения о подключении *atom.xml* файл **расширения и обновления**, см. в разделе [закрытые коллекции](../extensibility/private-galleries.md).  
  
-   Папку, содержащую все файлы изображений, которые были извлечены из расширений (например, снимки экрана). *Atom.xml* файл содержит относительных ссылок на эти образы, чтобы они были доступны в **расширения и обновления**.  
  
 Например предположим, что следующие два модуля, собранными в папку:  
  
-   *Template_Wizard_239.VSIX*, который является пустой шаблон проекта VSIX.  
  
-   *SelectionHighlight.vsix*, которое представляет собой инструмент, чтобы выделить все экземпляры отдельного слова.  
  
 Содержание *atom.xml* файла будет выглядеть следующим образом:  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>   
<feed xmlns="http://www.w3.org/2005/Atom">  
<title type="text" />   
<id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
<updated>2011-04-14T21:25:48Z</updated>   
<entry>  
<id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
<title type="text">Highlight all occurrences of selected word</title>   
<summary type="text">This extends the editor to highlight ....</summary>   
<published>2011-04-14T14:24:51-07:00</published>   
<updated>2011-04-14T14:24:22-07:00</updated>   
<author>  
<name>Microsoft</name>   
</author>  
<link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />   
<link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />   
<content type="application/octet-stream" src="SelectionHighlight.vsix" />   
<Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010">  
<Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>   
<Version>1.31</Version>   
<References />   
<Rating xsi:nil="true" />   
<RatingCount xsi:nil="true" />   
<DownloadCount xsi:nil="true" />   
</Vsix>  
</entry>  
<entry>  
<id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>   
...  
</entry>  
</feed>
```  
  
 Обратите внимание на то, что теги двух ссылок ссылаются на снимки экрана в папке созданного образов.  
  
## <a name="see-also"></a>См. также  
 [Закрытые коллекции](../extensibility/private-galleries.md)
