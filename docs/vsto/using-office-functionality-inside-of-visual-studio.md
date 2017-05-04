---
title: "Использование функциональных возможностей Office в Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Office - приложения [разработка решений Office в Visual Studio]"
  - "функциональные возможности Office (Visual Studio)"
  - "безопасность [разработка решений Office в Visual Studio], защита документов"
ms.assetid: 593fd583-57e5-4ed5-8489-89f73b886c6c
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Использование функциональных возможностей Office в Visual Studio
  При создании проекта уровня документа и документ, и связанное приложение размещаются в среде Visual Studio, чтобы разработчик мог проектировать документ и работать с ним напрямую.  При открытии приложения Microsoft Office в Visual Studio оно обычно выполняется, как ожидается.  Однако некоторые функциональные возможности приложения могут оказаться недоступными или вести себя неожиданным образом.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Защита документов  
 В Microsoft Office Word и Microsoft Office Excel предлагаются функции защиты документов, которые могут использоваться в проектах.  Однако если защита документа включена в то время, как документ открыт в Visual Studio, она может помешать внесению некоторых изменений в проект.  Дополнительные сведения см. в разделе [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md).  
  
## Управление правами на доступ к данным  
 В Microsoft Office Word и Microsoft Office Excel доступна функция управления правами на доступ к данным \(IRM\).  IRM позволяет защитить конфиденциальную информацию от просмотра или изменения со стороны несанкционированных пользователей.  Однако функция IRM также может помешать выполнению кода.  Дополнительные сведения см. в разделе [Общие сведения об управлении правами на доступ к данным и расширениях управляемого кода](../vsto/information-rights-management-and-managed-code-extensions-overview.md).  
  
## Защита паролем  
 Документы Microsoft Office Word и рабочие книги Microsoft Office Excel можно настроить так, что они не смогут быть открыты при незнании пароля.  Защита паролем обрабатывается в Word и Excel разными способами и может повлиять на процесс разработки.  Дополнительные сведения см. в разделе [Защита паролей в документах Office](../vsto/password-protection-on-office-documents.md).  
  
## См. также  
 [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md)   
 [Общие сведения об управлении правами на доступ к данным и расширениях управляемого кода](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Защита паролей в документах Office](../vsto/password-protection-on-office-documents.md)   
 [Практическое руководство. Открытие решений Office без выполнения кода](../vsto/how-to-open-office-solutions-without-running-code.md)  
  
  