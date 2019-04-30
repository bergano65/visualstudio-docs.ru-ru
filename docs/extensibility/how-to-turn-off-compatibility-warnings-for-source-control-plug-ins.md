---
title: Отключение предупреждений о совместимости для подключаемых модулей системы управления версиями | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a1a113dc3b4a4b3a8a4482dd092878851d740c6e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62911700"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Практическое руководство. Отключение предупреждений о совместимости для подключаемых модулей системы управления версиями
Пользователь может появиться несколько предупреждений о совместимости при создании системы управления версиями в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Представления предупреждений зависят от возможностей подключаемый модуль системы управления версиями и может быть отключен как подробные здесь.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Для отключения этого предупреждения: «Для обеспечения оптимальной интеграции системы управления с помощью Visual Studio»

- Задайте следующий параметр реестра (при необходимости добавив значение):

   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001**

   Это предупреждение отображается для всех отличных[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] подключаемых модулей.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Для отключения этого предупреждения: «Установленной системы управления версиями не поддерживает все возможности»

- Задайте следующие два значения (при необходимости добавления значений):

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:00000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001**

     Это предупреждение отображается в том случае, если подключаемый модуль системы управления версиями не поддерживает явным образом повторный вход для нескольких проектов (то есть, если его можно вернуть только один файл и проекта за раз).

     Она лучше всего подходит для поддержки повторного входа (`SCC_CAP_REENTRANT` возможность); это приведет к удалению этого предупреждения. Тем не менее если эта поддержка не поддерживается, можно задать эти записи реестра.

## <a name="see-also"></a>См. также
- [Флаги возможностей](../extensibility/capability-flags.md)