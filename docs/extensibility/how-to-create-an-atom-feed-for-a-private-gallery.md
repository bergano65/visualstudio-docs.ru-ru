---
title: 'Как: Создать атомную ленту для частной галереи (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72fbf2d3973ffd84de1cf6f33788c43511c3ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711014"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Как: Создать атомный канал для частной галереи
Можно создать канал Atom (RSS) в месторасположении интрасети, содержащее расширения, и добавить канал в **расширения и обновления** в качестве частной галереи. Дополнительные сведения см. в статье [Закрытые коллекции](../extensibility/private-galleries.md).

## <a name="create-an-atom-feed"></a>Создание корма Atom
 Чтобы создать канал Atom как частную галерею, вы сначала соберете ваши расширения *(файлы .vsix)* в папку. Вы можете организовать их в subfolders, если вы хотите. Вам также понадобятся следующие ресурсы:

- Файл *atom.xml,* который делает расширения доступными в качестве частной галереи. Для получения информации о том, как подключить файл *atom.xml* к **расширениям и обновлениям,** см. [Private galleries](../extensibility/private-galleries.md)

- Папка, содержащая все файлы изображений, извлеченные из расширений (например, снимки экрана). Файл *atom.xml* содержит относительные ссылки на эти изображения, чтобы они были доступны в **расширениях и обновлениях.**

  Например, предположим, что вы собрали следующие два расширения в папку:

- *Template_Wizard_239.vsix*, который является пустым шаблоном проекта VSIX.

- *SelectionHighlight.vsix*, который является инструментом, чтобы выделить все экземпляры выбранного слова.

  Содержимое файла *atom.xml* будет напоминать следующий пример:

```xml
<?xml version="1.0" encoding="UTF-8"?>
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
    <Vsix xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
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

 Обратите внимание, что два тега ссылки относятся к скриншотам в генерируемой папке изображений.

## <a name="see-also"></a>См. также
- [Частные галереи](../extensibility/private-galleries.md)
