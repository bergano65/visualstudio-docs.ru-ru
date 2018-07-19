---
title: 'Как: разрешить выполнения кода программной части документов с ограниченными разрешениями'
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
- permissions [Office development in Visual Studio]
- IRM [Office development in Visual Studio]
- code [Office development in Visual Studio], running behind restricted documents
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3b02afb7008233c720feae179b4726f9958a44af
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255290"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Как: разрешить выполнения кода программной части документов с ограниченными разрешениями
  Ограничение разрешений для документа или книги, можно использовать функции управления правами на доступ к данным (IRM) в Microsoft Office. По умолчанию кода программной части защищенный документ Microsoft Office Word или книгу Microsoft Office Excel не поддерживается для запуска. Значение по умолчанию можно изменить, чтобы ваши расширения управляемого кода можно получить доступ к объектной модели, и решение будет работать.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Необходимо быть автор документа или книги или иметь полный доступ, чтобы иметь возможность изменить параметры разрешений.  
  
## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Для разрешения выполнения кода программной части документов с ограниченными разрешениями  
  
1.  Откройте документ или книгу в Word или Excel.  
  
2.  Нажмите кнопку **файл** вкладке, выберите пункт **Подготовка**, пункты **ограничить разрешения**, а затем нажмите кнопку **ограниченный доступ**.  
  
    > [!NOTE]  
    >  При первом использовании вам предлагается установить клиент Windows Rights Management. После установки клиента, может потребоваться повторить шаги.  
  
3.  В **разрешение** выберите **ограничить разрешения для этого документа**, а затем нажмите кнопку **Дополнительно**.  
  
4.  В разделе **дополнительные разрешения для пользователей**выберите **программный доступ к содержимому**.  
  
 Разрешает программный доступ к объектной модели Word или Excel.  
  
## <a name="see-also"></a>См. также  
 [Управление правами и общие сведения о расширениях управляемого кода](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md)   
 [Защита паролей в документах Office](../vsto/password-protection-on-office-documents.md)   
 [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Безопасные решения Office](../vsto/securing-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)  
  
  