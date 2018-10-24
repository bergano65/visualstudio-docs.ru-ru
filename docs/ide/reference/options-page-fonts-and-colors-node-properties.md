---
title: Страница "Параметры", свойства узла "Шрифты и цвета"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 05724c81b9983414c4e0c86870b630e29c33ade3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926583"
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

|Имя элемента свойства|Значение|Описание:|
| - |-----------|-----------------|
|FontFamily|Get/Set (String)|Имя шрифта, например "Courier New".|
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|Значение <xref:EnvDTE.vsFontCharSet>, указывающее используемый тип кодировки, например иврит или русский язык.|
|FontSize|Get/Set (Short)|Размер шрифта в пунктах. Например, 10 или 12.|

## <a name="see-also"></a>См. также

- [Управление параметрами](http://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [Определение имен элементов свойств на страницах параметров](http://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [Страница "Параметры", свойства узла "Среда"](../../ide/reference/options-page-environment-node-properties.md)
- [Страница "Параметры", свойства узла "Текстовый редактор"](../../ide/reference/options-page-text-editor-node-properties.md)