---
title: "Как: разрешать выполнение с выделенным документов с ограниченными разрешениями кода | Документы Microsoft"
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
- permissions [Office development in Visual Studio]
- IRM [Office development in Visual Studio]
- code [Office development in Visual Studio], running behind restricted documents
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
ms.assetid: d037eae5-cf83-4be0-85ba-05e9f7d570e1
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1d5ab02ea2eb2d34a82607b8f7fd4fbf3f02dd76
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Практическое руководство. Выполнение с выделенным кодом документов с ограниченными разрешениями
  Компонент управления правами на доступ к данным (IRM) Microsoft Office можно использовать для ограничения разрешений для документа или книги. По умолчанию код, стоящий за защищенный документ Microsoft Office Word или книге Microsoft Office Excel не поддерживается для запуска. Значение по умолчанию можно изменить, чтобы расширений управляемого кода можно получить доступ к объектной модели и решение будет работать.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Должен быть автор документа или книги или иметь полный доступ, чтобы иметь возможность изменить параметры разрешений.  
  
### <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Для разрешения выполнения кода программной части документов с ограниченными разрешениями  
  
1.  Откройте документ или книгу в приложении Word или Excel.  
  
2.  Нажмите кнопку **файл** вкладке, выберите пункт **подготовки**, пункты **ограничить разрешения**, а затем нажмите кнопку **ограниченный доступ**.  
  
    > [!NOTE]  
    >  При первом использовании предлагается установить клиент управления правами Windows. После установки клиента, может потребоваться повторить шаги.  
  
3.  В **разрешение** выберите **ограничить разрешения для этого документа**, а затем нажмите кнопку **Дополнительно**.  
  
4.  В разделе **дополнительные разрешения для пользователей**выберите **программный доступ к содержимому**.  
  
 Разрешает программный доступ к объектной модели Word или Excel.  
  
## <a name="see-also"></a>См. также  
 [Управление правами и Обзор расширений управляемого кода](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md)   
 [Защита паролем в документах Office](../vsto/password-protection-on-office-documents.md)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)  
  
  