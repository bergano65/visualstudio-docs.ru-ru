---
title: Управление правами на информацию & расширения управляемого кода
description: Сведения о Rights Management (IRM) — функции, которая может помочь предотвратить несанкционированный просмотр или изменение конфиденциальной информации.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fc300ac83674b8faf2bd4c0fc6128f60c28ee92b
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523046"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Обзор управления правами на информацию и расширений управляемого кода
  Microsoft Office Word и Microsoft Office Excel предоставляют сведения Rights Management (IRM) — функцию, которая может помочь предотвратить несанкционированный просмотр или изменение конфиденциальной информации. Дополнительные сведения о работе Rights Management данных см. в разделе Справка в определенном приложении Office.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="run-code-behind-documents-with-restricted-permissions"></a>Выполнение документов программной части с ограниченными разрешениями
 Если решение содержит документ или книгу, в которой используется IRM, по умолчанию Word и Excel не разрешается выполнять какой-либо код. Если вы являетесь автором документа или имеете доступ с полным доступом, вы можете изменить значение по умолчанию, чтобы ваше решение работало. Дополнительные сведения см. [в разделе инструкции. разрешение выполнения кода для документов с ограниченными разрешениями](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

 IRM предотвращает использование <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> для получения или обработки данных, кэшированных в документе.

## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Конечные пользователи ограничивают разрешения для документов, использующих расширения управляемого кода
 Любой пользователь, обладающий полным доступом к документу или книге в решении, может использовать IRM для ограничения разрешений. Например, если конечный пользователь в отделе бухгалтерского учета использует решение, которое автоматически заполняет лист данными из базы данных, этот пользователь может захотеть разрешить доступ на изменение только пользователям в своем отделе и доступу для чтения к другим. Когда пользователь добавляет ограниченные разрешения, по умолчанию код, лежащий в основе листа, не может быть запущен и лист не будет заполнен данными.

 Чтобы устранить эту проблему, пользователь с правом полного доступа к документу или книге должен изменить параметры разрешений по умолчанию, чтобы разрешить программный доступ к объектной модели. Дополнительные сведения см. [в разделе инструкции. разрешение выполнения кода для документов с ограниченными разрешениями](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

## <a name="see-also"></a>См. также раздел
- [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md)
- [Защита паролем в документах Office](../vsto/password-protection-on-office-documents.md)
- [Безопасные решения Office](../vsto/securing-office-solutions.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
