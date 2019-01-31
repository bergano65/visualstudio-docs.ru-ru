---
title: Управление ресурсами приложения (.NET) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8319e4e71b313e0c4614f720cb371b339c09d391
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54784781"
---
# <a name="managing-application-resources-net"></a>Управление ресурсами приложения (.NET)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Файлы ресурсов — это файлы, которые являются частью приложения, но не компилируются, например файлы значков или звуковые файлы. Так как они не включаются в процесс компиляции, их можно изменять, не компилируя повторно двоичные файлы. Если вы планируете локализовать приложение, файлы ресурсов следует использовать для всех строк и других ресурсов, которые потребуется изменить при локализации.  
  
 Более подробную информацию о ресурсах в классических приложениях .NET см. в разделе [Ресурсы в приложениях для настольных систем](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890). Более подробную информацию о ресурсах в классических приложениях C++ см. в разделе [Working with Resource Files](http://msdn.microsoft.com/library/2699a539-b369-4b78-80f0-df03eb7b6780).  
  
 Модель ресурсов в приложениях Магазина Windows отличается от используемой в классических приложениях. Информацию о ресурсах в приложениях Магазина Windows см. в статье [Определение ресурсов приложений](https://msdn.microsoft.com/library/windows/apps/hh465228.aspx) на веб-сайте Центра разработки для Windows.  
  
## <a name="working-with-resources"></a>Работа с ресурсами  
 В проекте управляемого кода откройте окно свойств проекта (щелкните правой кнопкой мыши узел проекта в **обозревателе решений** и выберите пункт **Свойства**либо введите **свойства проекта** в окне **Быстрый запуск** либо нажмите клавиши ALT+ВВОД в окне **Обозреватель решений** ). Перейдите на вкладку **Ресурсы** . Вы можете добавить файл RESX, если проект его еще не содержит, добавить и удалить различные типы ресурсов, а также изменить существующие ресурсы.  
  
 Чтобы узнать, как работать с ресурсами в проектах C++, см. в разделе [как: Создание ресурса](http://msdn.microsoft.com/library/aad44914-9145-45a3-a7d8-9de89b366716)
