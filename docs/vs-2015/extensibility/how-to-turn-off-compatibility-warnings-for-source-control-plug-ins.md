---
title: Пошаговое руководство. Отключение предупреждений о совместимости для подключаемых модулей системы управления версиями | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204049"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Практическое руководство. Отключение предупреждений о совместимости для подключаемых модулей системы управления версиями
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пользователь может столкнуться с несколькими предупреждениями о совместимости при использовании системы управления версиями в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Представленные предупреждения зависят от возможностей подключаемого модуля системы управления версиями и могут быть отключены, как описано здесь.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Чтобы отключить предупреждение: "чтобы обеспечить оптимальную интеграцию системы управления версиями с Visual Studio..."  
  
- Задайте следующую запись реестра (при необходимости добавьте значение):  
  
     HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001  
  
     Это предупреждение отображается для всех не [!INCLUDE[vsvss](../includes/vsvss-md.md)] подключаемых модулей.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Чтобы отключить предупреждение: "установленный поставщик системы управления версиями не поддерживает все возможности..."  
  
- Задайте следующие два значения реестра (при необходимости добавьте значения):  
  
     HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000  
  
     HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001  
  
     Это предупреждение отображается, если подключаемый модуль системы управления версиями не поддерживает повторное повторное вход для нескольких проектов (то есть если он может одновременно выполнять возврат только одного файла и проекта).  
  
     Рекомендуется поддерживать повторный вход ( `SCC_CAP_REENTRANT` возможность); это приведет к удалению этого предупреждения. Однако если такая поддержка невозможна, можно установить эти записи реестра.  
  
## <a name="see-also"></a>См. также:  
 [Флаги возможностей](../extensibility/capability-flags.md)
