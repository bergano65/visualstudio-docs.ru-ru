---
title: "Управление правами и Обзор расширений управляемого кода | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 561f17acd17cb34892d3f2d4f0eefa05dfced0e4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Общие сведения об управлении правами на доступ к данным и расширениях управляемого кода
  Microsoft Office Word и Microsoft Office Excel предоставляют управления правами (IRM), функцию, которая может помочь предотвратить несанкционированные пользователи от просмотра или изменения конфиденциальные сведения. Дополнительные сведения о работе управления правами см.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="running-code-behind-documents-with-restricted-permissions"></a>Выполнение кода программной части документов с ограниченными разрешениями  
 Если решение содержит документ или книгу, по умолчанию использует функции IRM, Word и Excel не допускают выполнение кода. Если вы являетесь автором документа или имеют полный доступ, можно изменить значение по умолчанию, что решение. Дополнительные сведения см. в разделе [как: разрешить код для запуска под документами с ограниченными разрешениями](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 IRM не позволяет <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> для извлечения или управления данные, кэшированные в документе.  
  
## <a name="end-users-restricting-permissions-to-documents-that-use-managed-code-extensions"></a>Конечные пользователи, ограничив разрешения для документов с помощью расширений управляемого кода  
 Любой пользователь, имеющий полный доступ в документ или книгу в решении можно использовать IRM позволяет ограничить разрешения. Например если пользователь в бухгалтерии использует решение для автоматического заполнения книги данными из базы данных, этот пользователь может потребоваться разрешить изменить доступ только для пользователей в свой отдел и доступ для чтения к другим пользователям. Когда пользователь добавляет ограниченные разрешения, по умолчанию невозможна, лист с выделенным кодом, а листа будут заполнены данными.  
  
 Чтобы исправить эту проблему, пользователь с правами полного доступа документ или книгу необходимо изменить настройки разрешений по умолчанию, чтобы разрешить программный доступ к объектной модели. Дополнительные сведения см. в разделе [как: разрешить код для запуска под документами с ограниченными разрешениями](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## <a name="see-also"></a>См. также  
 [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md)   
 [Защита паролем в документах Office](../vsto/password-protection-on-office-documents.md)   
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)  
  
  