---
title: "Установка и развертывание. Вопросы и ответы | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "развертывание [Visual Studio SDK]"
  - "LCID [Visual Studio SDK]"
  - "установка [Visual Studio SDK]"
ms.assetid: 4ac62bf3-e335-4899-9074-89bcd004dc65
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# Установка и развертывание. Вопросы и ответы
В этом разделе рассматриваются вопросы от [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] общество пользователей об установке и развертывании.  Раздел будет по\-прежнему должен быть обновлен новым содержимым из сообщества.  
  
## Содержимое  
  
-   [Определение код языка установки Visual Studio программными средствами](#DeterminingtheLCIDofaVisualStudioInstallationProgrammatically)  
  
##  <a name="DeterminingtheLCIDofaVisualStudioInstallationProgrammatically"></a> Определение код языка установки Visual Studio программными средствами  
 Q. Существует возможность программно указать lcid a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] установка?  
  
 А. <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale2.GetUILocale%2A> OR  <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale.GetUILocale%2A>возвращает код языка  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в настоящий момент используется.  
  
## См. также  
 [Выпуск продукта](../misc/releasing-a-visual-studio-integration-product.md)