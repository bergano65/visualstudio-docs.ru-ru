---
title: Browse and Select a .NET Type Dialog Box | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d8e25ad181202a2c7994c116e2220426ca3d8509
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297612"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Диалоговое окно "Обзор и выбор типа .NET"
In the **Properties** window, dialog boxes, or designers such as the variable designer, when you select **Browse for Types…** from a list of data types, is the **Browse and Select a .NET Type** dialog box (referred to in an abbreviated form as the “type browser”). В этом диалоговом окне из представления в виде дерева сборок и проектов можно выбрать тип.

 Данное диалоговое окно используется во множестве пользовательских сценариев, включая следующие.

- При задании типа переменной или аргумента.

- При выборе типа для универсального действия.

- При добавлении захвата в действие <xref:System.Activities.Statements.TryCatch>.

> [!NOTE]
> Браузер типов может отображать типы массива массивов Visual Basic, но не типы многомерных массивов. See [Jagged Arrays](https://go.microsoft.com/fwlink/?LinkId=195226) and [Multidimensional Arrays](https://go.microsoft.com/fwlink/?LinkId=195227) for details.

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Выбор значения или ссылочного типа из браузера типов

#### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Выбор значения или ссылочного типа из браузера типов

1. In the **Type Name** box, enter the name of the type that you want to use.

2. Выполните одно из следующих действий.

    - Once the name of the type that you want to use appears in the tree in the **Type Name** box, double-click the type to select it.

    - Type enough characters in the **Type Name** box to uniquely identify the type that you want to use and then press enter to select the type

#### <a name="to-select-a-generic-type-from-the-type-browser"></a>Выбор универсального типа из браузера типов

1. In the **Type Name** box, type in the name of the type that you want to use.

2. Once the name of the type that you want to use appears in the tree in the **Type Name** box, click the type to select it to cause drop-down boxes appear.

     Select the type that you want to use to close the generic from the drop-down boxes, and then click **OK**.

## <a name="types-displayed-in-the-type-browser"></a>Типы, отображенные в браузере типов
 Типы, отображенные в браузере типов, могут изменяться в зависимости от способа запуска браузера. If the type browser was launched from a workflow project inside of **vs2010**, by default all of the types in the referenced assemblies and referenced projects are shown. If the type browser was launched from outside of a **vs2010** project system (such as in a rehosted workflow application or in a standalone workflow file), then by default the types from all of the assemblies loaded in the AppDomain are shown.

 Разработчики конструкторов операций могут отфильтровать типы в браузере типов. Для каждого данного действия можно увидеть поднабор типов. Например, в действии <xref:System.Activities.Statements.TryCatch> в браузере типов отображаются только типы, производные от <xref:System.Exception>.

## <a name="filtering-search-results-in-the-type-browser"></a>Фильтрация результатов поиска в браузере типов
 The list of types in the **Type Name** box gets shorter as you type more characters to find a match. В отфильтрованном списке отображаются только те типы, чье полное или короткое имя начинается с введенной строки.

 Пример:

1. Typing **Operation** matches <xref:System.OperationCanceledException> but not <xref:System.InvalidOperationException>. Чтобы введенное слово совпало с <xref:System.InvalidOperationException>, начните строку с System.I или Invalid.

2. Typing **Generic** matches <xref:System.GenericUriParser> but not types in the <xref:System.Collections.Generic> namespace. Чтобы выполнить поиск типов в пространстве имен <xref:System.Collections.Generic>, введите полное имя пространства имен.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Выбор контракта службы с помощью диалогового окна браузера типов
 При выборе типа контракта службы браузер типов отображает только типы, имеющие атрибут <xref:System.ServiceModel.ServiceContractAttribute>.

## <a name="see-also"></a>См. также раздел
 [Использование конструкторов действий](../workflow-designer/using-the-activity-designers.md)