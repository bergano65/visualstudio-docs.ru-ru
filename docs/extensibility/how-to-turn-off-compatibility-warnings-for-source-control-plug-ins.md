---
title: Отключить предупреждения для подключаемых модулей системы управления версиями
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33cf57aa86608cca96924faa2caeb9eec7fbdc0e
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2020
ms.locfileid: "89742777"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Пошаговое руководство. Отключение предупреждений о совместимости для подключаемых модулей системы управления версиями

Пользователь может столкнуться с несколькими предупреждениями о совместимости при использовании системы управления версиями в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Представленные предупреждения зависят от возможностей подключаемого модуля системы управления версиями и могут быть отключены, как описано здесь.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Отключение предупреждения: "чтобы обеспечить оптимальную интеграцию системы управления версиями с Visual Studio"

- Задайте следующую запись реестра (при необходимости добавьте значение):

   **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001**

   Это предупреждение отображается для всех не [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] подключаемых модулей.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Чтобы отключить предупреждение: "установленный поставщик системы управления версиями не поддерживает все возможности"

- Задайте следующие два значения реестра (при необходимости добавьте значения):

     **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000**

    **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001**

     Это предупреждение отображается, если подключаемый модуль системы управления версиями не поддерживает повторное повторное вход для нескольких проектов (то есть если он может одновременно выполнять возврат только одного файла и проекта).

     Рекомендуется поддерживать повторный вход ( `SCC_CAP_REENTRANT` возможность); это приведет к удалению этого предупреждения. Однако если такая поддержка невозможна, можно установить эти записи реестра.

## <a name="see-also"></a>См. также

- [Флаги возможностей](../extensibility/capability-flags.md)
