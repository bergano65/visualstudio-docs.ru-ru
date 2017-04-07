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
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 85a03270b20b050cc5ca96f57311c98c0d9b53d1
ms.lasthandoff: 04/05/2017

---
# <a name="managing-application-resources-net"></a>Управление ресурсами приложения (.NET)
Файлы ресурсов — это файлы, которые являются частью приложения, но не компилируются, например файлы значков или звуковые файлы. Так как они не включаются в процесс компиляции, их можно изменять, не компилируя повторно двоичные файлы. Если вы планируете локализовать приложение, файлы ресурсов следует использовать для всех строк и других ресурсов, которые потребуется изменить при локализации.  
  
 Более подробную информацию о ресурсах в классических приложениях .NET см. в разделе [Ресурсы в приложениях для настольных систем](http://msdn.microsoft.com/Library/8ad495d4-2941-40cf-bf64-e82e85825890). Более подробную информацию о ресурсах в классических приложениях C++ см. в разделе [Работа с файлами ресурсов](/cpp/windows/working-with-resource-files).  
  
 Модель ресурсов в приложениях Магазина Windows отличается от используемой в классических приложениях. Информацию о ресурсах в приложениях Магазина Windows см. в статье [Определение ресурсов приложений](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx) на веб-сайте Центра разработки для Windows.  
  
## <a name="working-with-resources"></a>Работа с ресурсами  
 В проекте управляемого кода откройте окно свойств проекта (щелкните правой кнопкой мыши узел проекта в **обозревателе решений** и выберите пункт **Свойства**либо введите **свойства проекта** в окне **Быстрый запуск** либо нажмите клавиши ALT+ВВОД в окне **Обозреватель решений** ). Перейдите на вкладку **Ресурсы** . Вы можете добавить файл RESX, если проект его еще не содержит, добавить и удалить различные типы ресурсов, а также изменить существующие ресурсы.  
  
 Узнать, как работать с ресурсами в проектах C++, можно в разделе [Практическое руководство. Создание ресурса](http://msdn.microsoft.com/Library/aad44914-9145-45a3-a7d8-9de89b366716).
