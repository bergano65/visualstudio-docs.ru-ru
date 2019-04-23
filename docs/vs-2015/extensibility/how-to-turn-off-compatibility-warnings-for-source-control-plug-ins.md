---
title: Практическое руководство. Отключение предупреждений о совместимости для подключаемых модулей системы управления версиями | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4397b2710a7de4addd97bfcbdb4f8e80e2b9c70
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060583"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Практическое руководство. Отключение предупреждений о совместимости для подключаемых модулей системы управления версиями
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пользователь может появиться несколько предупреждений о совместимости при создании системы управления версиями в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Представления предупреждений зависят от возможностей подключаемый модуль системы управления версиями и может быть отключен как подробные здесь.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Для отключения этого предупреждения: «Для обеспечения оптимальной интеграции системы управления с помощью Visual Studio...»  
  
- Задайте следующий параметр реестра (при необходимости добавив значение):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001  
  
     Это предупреждение отображается для всех отличных[!INCLUDE[vsvss](../includes/vsvss-md.md)] подключаемых модулей.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Для отключения этого предупреждения: «Установленной системы управления версиями не поддерживает все возможности...»  
  
- Задайте следующие два значения (при необходимости добавления значений):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:00000000  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001  
  
     Это предупреждение отображается в том случае, если подключаемый модуль системы управления версиями не поддерживает явным образом повторный вход для нескольких проектов (то есть, если его можно вернуть только один файл и проекта за раз).  
  
     Она лучше всего подходит для поддержки повторного входа (`SCC_CAP_REENTRANT` возможность); это приведет к удалению этого предупреждения. Тем не менее если эта поддержка не поддерживается, можно задать эти записи реестра.  
  
## <a name="see-also"></a>См. также  
 [Флаги возможностей](../extensibility/capability-flags.md)
