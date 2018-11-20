---
title: Управление ресурсами приложения (.NET)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b9a80a84276648f8a0f0d5a94992b5f58cbcfefa
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348140"
---
# <a name="manage-application-resources-net"></a>Управление ресурсами приложения (.NET)

Файлы ресурсов — это файлы, которые являются частью приложения, но не компилируются, например файлы значков или звуковые файлы. Так как они не включаются в процесс компиляции, их можно изменять, не компилируя повторно двоичные файлы. Если вы планируете локализовать приложение, файлы ресурсов следует использовать для всех строк и других ресурсов, которые потребуется изменить при локализации.

> [!NOTE]
> Этот раздел относится к Visual Studio в Windows. Информацию о Visual Studio для Mac см. в статье [Управление ресурсами приложения (Visual Studio для Mac)](/visualstudio/mac/managing-app-resources).

Более подробную информацию о ресурсах в классических приложениях .NET см. в разделе [Ресурсы в классических приложениях](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Работа с ресурсами

В проекте управляемого кода откройте окно свойств проекта. Для этого вы можете:

- щелкнуть правой кнопкой мыши узел проекта в **обозревателе решений** и выбрать пункт **Свойства**;
- ввести фразу "свойства проекта" в окне **Быстрый запуск**;
- нажать клавиши **ALT**+**ВВОД** в **обозревателе решений**.

Перейдите на вкладку **Ресурсы** . Вы можете добавить файл *RESX*, если проект его еще не содержит, добавить и удалить различные типы ресурсов, а также изменить существующие ресурсы.

## <a name="resources-in-other-project-types"></a>Ресурсы в других типах проектов

Управление ресурсами в проектах .NET осуществляется не так, как в проектах других типов. Дополнительные сведения о ресурсах:

- приложения универсальной платформы Windows (UWP) — [Ресурсы приложения и система управления ресурсами](/windows/uwp/app-resources/);
- проекты C++ — [Работа с файлами ресурсов](/cpp/windows/working-with-resource-files) и [Практическое руководство. Создание ресурса](/cpp/windows/how-to-create-a-resource).

## <a name="see-also"></a>См. также

- [Ресурсы в классических приложениях (.NET Framework)](/dotnet/framework/resources/index)
- [Управление ресурсами приложения (Visual Studio для Mac)](/visualstudio/mac/managing-app-resources)
