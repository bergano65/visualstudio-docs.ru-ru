---
title: Использование функциональных возможностей Office в Visual Studio
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6a1db785b4758236c4a50e694d868cecc269324a
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767511"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Использование функциональных возможностей Office в Visual Studio
  При создании проекта уровня документа, документ и связанное приложение размещаются в Visual Studio, чтобы можно было разрабатывать и работать непосредственно с документом. Если у вас есть Microsoft Office, откройте приложение в Visual Studio, обычно работает надлежащим образом. Тем не менее некоторые функциональные возможности приложений могут оказаться недоступными или.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="document-protection"></a>Защита документов  
 Microsoft Office Word и Microsoft Office Excel предоставляют функции защиты, которые можно использовать в проектах документов. Тем не менее если защита включена, когда документ открыт в Visual Studio, она может помешать внесения некоторых изменений в макет. Дополнительные сведения см. в разделе [защита в решениях уровня документа документов](../vsto/document-protection-in-document-level-solutions.md).  
  
## <a name="information-rights-management"></a>Управление правами  
 Управление правами на доступ к данным (IRM) в Microsoft Office Word и Microsoft Office Excel. IRM может помочь избежать несанкционированного просмотра и изменения важной информации. Однако IRM можно также предотвратить код работает. Дополнительные сведения см. в разделе [управление правами и Обзор расширений управляемого кода](../vsto/information-rights-management-and-managed-code-extensions-overview.md).  
  
## <a name="password-protection"></a>Защита паролем  
 Документы Microsoft Office Word и книг Microsoft Office Excel можно задать, чтобы они не может быть открыта тем, кто знает пароль. Защита паролем обрабатывается по-разному в Word и Excel и могут повлиять на процесс разработки. Дополнительные сведения см. в разделе [защита паролем в документах Office](../vsto/password-protection-on-office-documents.md).  
  
## <a name="see-also"></a>См. также  
 [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md)   
 [Управление правами и Обзор расширений управляемого кода](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Защита паролем в документах Office](../vsto/password-protection-on-office-documents.md)   
 [Как: решений откройте Office без выполнения кода](../vsto/how-to-open-office-solutions-without-running-code.md)  
  
  