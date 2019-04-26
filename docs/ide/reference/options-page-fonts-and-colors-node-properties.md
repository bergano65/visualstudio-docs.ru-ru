---
title: Страница "Параметры", свойства узла "Шрифты и цвета"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5363d71082128c13146c445fe312424be7e4340
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945598"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Страница "Параметры", свойства узла "Шрифты и цвета"
Этот документ описывает свойства шрифтов и цветов для окна инструментов, которое должно отображаться в списке **Шрифты и цвета** в категории **Среда** диалогового окна **Параметры**. Этим обеспечивается динамическая природа групп цветных элементов, которые могут меняться при установке и удалении пакетов VSPackage.

 Ниже показан пример зарегистрированного типа окна и свойств, доступных для каждого окна.

## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Текстовый редактор или принтер или диалоговые окна и окна инструментов
 `DTE.Properties("FontsAndColors", "TextEditor")`

 - или -

 `DTE.Properties("FontsAndColors", "Printer")`

 - или -

 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`

|Имя элемента свойства|Значение|Описание|
| - |-----------|-----------------|
|FontFamily|Get/Set (String)|Имя шрифта, например "Courier New".|
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|Значение <xref:EnvDTE.vsFontCharSet>, указывающее используемый тип кодировки, например иврит или русский язык.|
|FontSize|Get/Set (Short)|Размер шрифта в пунктах. Например, 10 или 12.|

## <a name="see-also"></a>См. также раздел

- [Управление параметрами](https://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [Определение имен элементов свойств на страницах параметров](https://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [Страница "Параметры", свойства узла "Среда"](../../ide/reference/options-page-environment-node-properties.md)
- [Страница "Параметры", свойства узла "Текстовый редактор"](../../ide/reference/options-page-text-editor-node-properties.md)