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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: efe2b176db9f6f22f9e38775d5fc8acad87655ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651390"
---
# <a name="managing-application-resources-net"></a>Управление ресурсами приложения (.NET)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Файлы ресурсов — это файлы, которые являются частью приложения, но не компилируются, например файлы значков или звуковые файлы. Так как они не включаются в процесс компиляции, их можно изменять, не компилируя повторно двоичные файлы. Если вы планируете локализовать приложение, файлы ресурсов следует использовать для всех строк и других ресурсов, которые потребуется изменить при локализации.

 Более подробную информацию о ресурсах в классических приложениях .NET см. в разделе [Resources in Desktop Apps](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890). Более подробную информацию о ресурсах в классических приложениях C++ см. в разделе [Working with Resource Files](https://msdn.microsoft.com/library/2699a539-b369-4b78-80f0-df03eb7b6780).

 Модель ресурсов в приложениях Магазина Windows отличается от используемой в классических приложениях. Информацию о ресурсах в приложениях Магазина Windows см. в статье [Определение ресурсов приложений](https://msdn.microsoft.com/library/windows/apps/hh465228.aspx) на веб-сайте Центра разработки для Windows.

## <a name="working-with-resources"></a>Работа с ресурсами
 В проекте управляемого кода откройте окно свойств проекта (щелкните правой кнопкой мыши узел проекта в **обозревателе решений** и выберите пункт **Свойства**либо введите **свойства проекта** в окне **Быстрый запуск** либо нажмите клавиши ALT+ВВОД в окне **Обозреватель решений** ). Перейдите на вкладку **ресурсы** . Вы можете добавить RESX-файл, если проект еще не содержит его, добавлять и удалять различные типы ресурсов, а также изменять существующие ресурсы.

 Узнать, как работать с ресурсами в проектах C++, можно в разделе [How to: Create a Resource](https://msdn.microsoft.com/library/aad44914-9145-45a3-a7d8-9de89b366716).
