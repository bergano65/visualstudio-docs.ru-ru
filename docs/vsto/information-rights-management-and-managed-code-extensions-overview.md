---
title: Управление правами и Обзор расширений управляемого кода
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 35a118774d50bcc697cd3ff5663fc26d8580ac88
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34263765"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Управление правами и Обзор расширений управляемого кода
  Microsoft Office Word и Microsoft Office Excel предоставляют управления правами (IRM), функцию, которая может помочь предотвратить несанкционированные пользователи от просмотра или изменения конфиденциальные сведения. Дополнительные сведения о работе управления правами см.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="run-code-behind-documents-with-restricted-permissions"></a>Выполнить код программной части документов с ограниченными разрешениями  
 Если решение содержит документ или книгу, по умолчанию использует функции IRM, Word и Excel не допускают выполнение кода. Если вы являетесь автором документа или имеют полный доступ, можно изменить значение по умолчанию, что решение. Дополнительные сведения см. в разделе [как: разрешить выполнения кода программной части документов с ограниченными разрешениями](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 IRM не позволяет <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> для извлечения или управления данные, кэшированные в документе.  
  
## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Конечные пользователи могут ограничить разрешения для документов с помощью расширений управляемого кода  
 Любой пользователь, имеющий полный доступ в документ или книгу в решении можно использовать IRM позволяет ограничить разрешения. Например если пользователь в бухгалтерии использует решение для автоматического заполнения книги данными из базы данных, этот пользователь может потребоваться разрешить изменить доступ только для пользователей в свой отдел и доступ для чтения к другим пользователям. Когда пользователь добавляет ограниченные разрешения, по умолчанию невозможна, лист с выделенным кодом, а листа будут заполнены данными.  
  
 Чтобы исправить эту проблему, пользователь с правами полного доступа документ или книгу необходимо изменить настройки разрешений по умолчанию, чтобы разрешить программный доступ к объектной модели. Дополнительные сведения см. в разделе [как: разрешить выполнения кода программной части документов с ограниченными разрешениями](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## <a name="see-also"></a>См. также  
 [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md)   
 [Защита паролем в документах Office](../vsto/password-protection-on-office-documents.md)   
 [Безопасные решения Office](../vsto/securing-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)  
  
  