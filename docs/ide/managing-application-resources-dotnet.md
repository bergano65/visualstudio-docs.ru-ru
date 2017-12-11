---
title: "Управление ресурсами приложения (.NET) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b599a919911fcc5d2833cfe69b75f7b32cced858
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="managing-application-resources-net"></a>Управление ресурсами приложения (.NET)
Файлы ресурсов — это файлы, которые являются частью приложения, но не компилируются, например файлы значков или звуковые файлы. Так как они не включаются в процесс компиляции, их можно изменять, не компилируя повторно двоичные файлы. Если вы планируете локализовать приложение, файлы ресурсов следует использовать для всех строк и других ресурсов, которые потребуется изменить при локализации.  
  
Более подробную информацию о ресурсах в классических приложениях .NET см. в разделе [Resources in Desktop Apps](/dotnet/framework/resources/index). Более подробную информацию о ресурсах в классических приложениях C++ см. в разделе [Working with Resource Files](/cpp/windows/working-with-resource-files).  
  
Модель ресурсов в приложениях UWP отличается от используемой в классических приложениях. Сведения о ресурсах в приложениях Windows 8.x см. в разделе [Определение ресурсов приложения (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx).  
  
## <a name="working-with-resources"></a>Работа с ресурсами  
В проекте управляемого кода откройте окно свойств проекта. Для этого вы можете:

- щелкнуть правой кнопкой мыши узел проекта в **обозревателе решений** и выбрать пункт **Свойства**;
- ввести фразу **свойства проекта** в окне **Быстрый запуск**;
- нажать клавиши **ALT+ВВОД** в окне **обозревателя решений**.

Перейдите на вкладку **Ресурсы** . Вы можете добавить файл RESX, если проект его еще не содержит, добавить и удалить различные типы ресурсов, а также изменить существующие ресурсы.  
  
Узнать, как работать с ресурсами в проектах C++, можно в разделе [How to: Create a Resource](/cpp/windows/how-to-create-a-resource).