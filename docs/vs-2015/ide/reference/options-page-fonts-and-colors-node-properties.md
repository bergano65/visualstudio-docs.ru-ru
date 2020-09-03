---
title: Страница "Параметры", свойства узла "Шрифты и цвета" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23aa4eff3339ad3cd3ab7d4106745dc6fa83df34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662431"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Страница "Параметры", свойства узла "Шрифты и цвета"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Этот документ описывает свойства шрифтов и цветов для окна инструментов, которое должно отображаться в списке **Шрифты и цвета** в категории **Среда** диалогового окна **Параметры**. Этим обеспечивается динамическая природа групп цветных элементов, которые могут меняться при установке и удалении пакетов VSPackage.

 Ниже показан пример зарегистрированного типа окна и свойств, доступных для каждого окна.

## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Текстовый редактор или принтер или диалоговые окна и окна инструментов
 `DTE.Properties("FontsAndColors", "TextEditor")`

 -или-

 `DTE.Properties("FontsAndColors", "Printer")`

 -или-

 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`

|Имя элемента свойства|Значение|Описание|
|------------------------|-----------|-----------------|
|FontFamily|Get/Set (String)|Имя шрифта, например "Courier New".|
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|Значение <xref:EnvDTE.vsFontCharSet>, указывающее используемый тип кодировки, например иврит или русский язык.|
|FontSize|Get/Set (Short)|Размер шрифта в пунктах. Например, 10 или 12.|

## <a name="see-also"></a>См. также:
 [Управление параметрами](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) параметры [Определение имен элементов свойств на](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) странице параметров страницы параметров страницы параметры [Свойства узла среды](../../ide/reference/options-page-environment-node-properties.md) [, свойства узла текстового редактора](../../ide/reference/options-page-text-editor-node-properties.md)
