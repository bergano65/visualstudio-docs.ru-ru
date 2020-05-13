---
title: Выключите предупреждения о совместимости для подключаемых модули управления исходным управлением (ru) Документы Майкрософт
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
ms.openlocfilehash: 22dd3821426aa1dae6265c520ddac60dd93e1c5e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710725"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Как: Выключить предупреждения о совместимости для плагинов управления исходным управлением
Пользователь может видеть несколько предупреждений о совместимости при использовании элемента управления исходом в. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Предупреждения, представленные зависит от возможностей плагина управления исходным источником и могут быть отключены, как описано здесь.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Отключить предупреждение: "Обеспечить оптимальную интеграцию управления исходным источником с Visual Studio"

- Установите следующую запись реестра (при необходимости добавляя значение):

   **HKEY_CURRENT_USER-Программное обеспечение,Microsoft-VisualStudio-8.0 -ИсточникКонтроль/DontDisplayCheckDotCOMPATIBLe - dword:00000001**

   Это предупреждение отображается для[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] всех не-плагинов.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Отключить предупреждение: "Поставщик управления установленным исходным источником не поддерживает все возможности"

- Установите следующие два значения реестра (при необходимости добавлении значений):

     **HKEY_CURRENT_USER-Программное обеспечение,Microsoft-VisualStudio-8.0 -ИсточникКонтроль-ПредупрежденОлдMsSCCIProvider - dword:00000000**

    **HKEY_CURRENT_USER-Программное обеспечение,Microsoft-VisualStudio-8.0 -ИсточникКонтроль-UseOldSCC - dword:00000001**

     Это предупреждение отображается, если плагин управления исходным элементом явно не поддерживает повторное размещение для нескольких проектов (т.е. если он может зарегистрировать только один файл и проект одновременно).

     Лучше всего поддерживать ретрансцию`SCC_CAP_REENTRANT` (возможности); это удалит это предупреждение. Однако, если эта поддержка непредставляется, эти записи реестра могут быть установлены.

## <a name="see-also"></a>См. также
- [Флаги возможностей](../extensibility/capability-flags.md)
