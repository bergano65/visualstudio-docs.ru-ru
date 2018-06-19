---
title: Отключить предупреждения совместимости для подключаемых модулей системы управления версиями | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2d3cffbd6a8b6c21aa6e958495b88eb51a5724a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129554"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Как: отключить предупреждения совместимости для подключаемых модулей системы управления версиями
Пользователь может столкнуться несколько предупреждений совместимости при использовании системы управления версиями в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Предупреждения представлены зависят от возможностей системы управления версиями и может быть отключен как подробные здесь.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Для отключения этого предупреждения: «для обеспечения оптимальной интеграции системы управления с помощью Visual Studio...»  
  
-   Задайте следующий параметр реестра (при необходимости добавления значения):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001  
  
     Это предупреждение отображается для всех отличных[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] подключаемых модулей.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Для отключения этого предупреждения: «установленной системы управления версиями не поддерживает все возможности...»  
  
-   Задайте следующие два значения (при необходимости добавления значений):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001  
  
     Это предупреждение отображается, если подключаемый модуль системы управления версиями не поддерживает явным образом повторный вход для нескольких проектов (то есть, если ее можно вернуть только один файл и проекта одновременно).  
  
     Рекомендуется для поддержки повторного входа (`SCC_CAP_REENTRANT` возможность); это приведет к удалению этого предупреждения. Тем не менее если эта поддержка невозможна, можно задать эти записи реестра.  
  
## <a name="see-also"></a>См. также  
 [Флаги возможностей](../extensibility/capability-flags.md)