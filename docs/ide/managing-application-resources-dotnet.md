---
title: "Управление ресурсами приложения (.NET) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
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
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 5cb2e044f5c55881adade6d3022fc453360a2e9c
ms.contentlocale: ru-ru
ms.lasthandoff: 05/30/2017

---
# Управление ресурсами приложения (.NET)
<a id="managing-application-resources-net" class="xliff"></a>
Файлы ресурсов — это файлы, которые являются частью приложения, но не компилируются, например файлы значков или звуковые файлы. Так как они не включаются в процесс компиляции, их можно изменять, не компилируя повторно двоичные файлы. Если вы планируете локализовать приложение, файлы ресурсов следует использовать для всех строк и других ресурсов, которые потребуется изменить при локализации.  
  
 Более подробную информацию о ресурсах в классических приложениях .NET см. в разделе [Ресурсы в приложениях для настольных систем](/dotnet/framework/resources/index). Более подробную информацию о ресурсах в классических приложениях C++ см. в разделе [Working with Resource Files](/cpp/windows/working-with-resource-files).  
  
 Модель ресурсов в приложениях Магазина Windows отличается от используемой в классических приложениях. Информацию о ресурсах в приложениях Магазина Windows см. в статье [Определение ресурсов приложений](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx) на веб-сайте Центра разработки для Windows.  
  
## Работа с ресурсами
<a id="working-with-resources" class="xliff"></a>  
 В проекте управляемого кода откройте окно свойств проекта (щелкните правой кнопкой мыши узел проекта в **обозревателе решений** и выберите пункт **Свойства**либо введите **свойства проекта** в окне **Быстрый запуск** либо нажмите клавиши ALT+ВВОД в окне **Обозреватель решений** ). Перейдите на вкладку **Ресурсы** . Вы можете добавить файл RESX, если проект его еще не содержит, добавить и удалить различные типы ресурсов, а также изменить существующие ресурсы.  
  
 Узнать, как работать с ресурсами в проектах C++, можно в разделе [Практическое руководство. Создание ресурса](/cpp/windows/how-to-create-a-resource).
