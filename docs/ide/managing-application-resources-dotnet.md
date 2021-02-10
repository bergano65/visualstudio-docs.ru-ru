---
title: Управление ресурсами приложения (.NET)
description: Сведения о том, как управлять файлами ресурсов приложений, которые не используются в процессе компиляции.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b970e9e502542da0452c1ed4f1ebb4585f00559b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903962"
---
# <a name="manage-application-resources-net"></a>Управление ресурсами приложения (.NET)

Файлы ресурсов — это файлы, которые являются частью приложения, но не компилируются, например файлы значков или звуковые файлы. Так как они не включаются в процесс компиляции, их можно изменять, не компилируя повторно двоичные файлы. Если вы планируете локализовать приложение, файлы ресурсов следует использовать для всех строк и других ресурсов, которые потребуется изменить при локализации.

> [!NOTE]
> Этот раздел относится к Visual Studio в Windows. Информацию о Visual Studio для Mac см. в статье [Управление ресурсами приложения (Visual Studio для Mac)](/visualstudio/mac/managing-app-resources).

Дополнительные сведения о ресурсах в приложениях .NET см. в разделе [Ресурсы в приложениях .NET](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Работа с ресурсами

В проекте управляемого кода откройте окно свойств проекта. Для этого вы можете:

- щелкнуть правой кнопкой мыши узел проекта в **обозревателе решений** и выбрать пункт **Свойства**;
- ввести фразу **свойства проекта** в поле поиска, открытого с помощью **CTRL**+**Q**;
- нажать клавиши **ALT**+**ВВОД** в **обозревателе решений**.

Перейдите на вкладку **Ресурсы** . Вы можете добавить файл *RESX*, если проект его еще не содержит, добавить и удалить различные типы ресурсов, а также изменить существующие ресурсы.

## <a name="resources-in-other-project-types"></a>Ресурсы в других типах проектов

Управление ресурсами в проектах .NET осуществляется не так, как в проектах других типов. Дополнительные сведения о ресурсах:

- приложения универсальной платформы Windows (UWP) — [Ресурсы приложения и система управления ресурсами](/windows/uwp/app-resources/);
- проекты C++ — [Работа с файлами ресурсов](/cpp/windows/working-with-resource-files) и [Практическое руководство. Создание ресурса](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>См. также

- [Ресурсы в приложениях (.NET Framework)](/dotnet/framework/resources/index)
- [Управление ресурсами приложения (Visual Studio для Mac)](/visualstudio/mac/managing-app-resources)
