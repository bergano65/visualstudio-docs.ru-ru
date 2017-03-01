---
title: "Отключить предупреждения о совместимости для подключаемых модулей системы управления версиями | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: e1dda3bd8c41efcf74a1b27f764fdfbf817f8d63
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Практическое руководство: отключение предупреждения о совместимости для подключаемых модулей системы управления версиями
Пользователь может просмотреть несколько предупреждения о совместимости при использовании системы управления версиями в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Предупреждения представленных зависят от возможностей подключаемый модуль системы управления версиями и может быть отключен как подробные здесь.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Чтобы отключить предупреждение: «для обеспечения оптимальной интеграции системы управления с помощью Visual Studio...»  
  
-   Задайте следующий параметр реестра (при необходимости можно добавлять значения):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD:&00000;001  
  
     Это предупреждение отображается для всех отличных[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] подключаемых модулей.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Чтобы отключить предупреждение: «установленные системы управления версиями не поддерживает все возможности...»  
  
-   Задайте следующие два значения (при необходимости можно добавлять значения):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD:&00000;000  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD:&00000;001  
  
     Это предупреждение отображается, если подключаемый модуль системы управления версиями не поддерживает явным образом повторный вход для нескольких проектов (то есть, если его можно вернуть только один файл и проекта одновременно).  
  
     Рекомендуется для поддержки повторного входа (`SCC_CAP_REENTRANT` возможности); это приведет к удалению этого предупреждения. Однако если эта поддержка невозможна, можно задать эти записи реестра.  
  
## <a name="see-also"></a>См. также  
 [Флаги возможностей](../extensibility/capability-flags.md)
