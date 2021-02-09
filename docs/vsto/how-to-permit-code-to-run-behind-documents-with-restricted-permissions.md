---
title: Разрешение выполнения кода позади документов с ограниченными разрешениями
description: Узнайте, как можно разрабатывать код для работы с документами с ограниченными разрешениями с помощью средств разработки Office в Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1a65e99712658567996598d2190447ff09cf9b05
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888892"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Как разрешите выполнение кода для документов с ограниченными разрешениями
  Для ограничения разрешений на документ или книгу можно использовать функцию Information Rights Management (IRM) Microsoft Office. По умолчанию не разрешается запускать код программной части ограниченного Microsoft Office документа Word или Microsoft Office книги Excel. Можно изменить значение по умолчанию, чтобы расширения управляемого кода могли получить доступ к объектной модели, и ваше решение будет работать.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Чтобы иметь возможность изменять параметры разрешений, необходимо быть автором документа или книги или иметь полный доступ к ним.

## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Разрешение выполнения кода на основе документов с ограниченными разрешениями

1. Откройте документ или книгу в Word или Excel.

2. Перейдите на вкладку **файл** , наведите указатель мыши на пункт **Подготовка**, выберите пункт **ограничить разрешения** и щелкните **ограниченный доступ**.

   > [!NOTE]
   > При первом использовании вам будет предложено установить клиент Windows Rights Management. После установки клиента может потребоваться повторить эти действия.

3. В диалоговом окне **разрешение** выберите **ограничить разрешения для этого документа**, а затем щелкните **Дополнительные параметры**.

4. В разделе **Дополнительные разрешения для пользователей** выберите **доступ к содержимому программным способом**.

   Word или Excel позволяет программный доступ к объектной модели.

## <a name="see-also"></a>См. также раздел
- [Обзор управления правами на информацию и расширений управляемого кода](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md)
- [Защита паролем в документах Office](../vsto/password-protection-on-office-documents.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
- [Безопасные решения Office](../vsto/securing-office-solutions.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)
