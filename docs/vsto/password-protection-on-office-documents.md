---
title: Защита паролем в документах Office
description: Узнайте, как задать пароль для документов Microsoft Word и книг Excel, чтобы они не могли быть открыты неавторизованными пользователями.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2cc320baf310af0ec2b4cdd84fabff951b2a9cb2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885291"
---
# <a name="password-protection-on-office-documents"></a>Защита паролем в документах Office
  Можно задать пароль для Microsoft Office документов Word и Microsoft Office книги Excel, чтобы их не могли открывать пользователи, не знающие пароль. Этот параметр называется **password on Open**.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Можно создавать проекты на уровне документа, используя существующие документы и книги с включенным **паролем при открытии** . Поведение в Visual Studio отличается для документов Word и Excel с включенным **паролем при открытии** .

 Сведения о включении **пароля при открытии** см. в справке Word или Excel.

## <a name="behavior-of-excel-and-word"></a>Поведение Excel и Word
 При каждом открытии книги Excel в Visual Studio с включенным **паролем при открытии** программа Excel запрашивает пароль. При сборке решения вам снова будет предложено ввести пароль, так как документ будет открыт во время сборки.

 При первом открытии документа Word в Visual Studio с включенным **паролем при открытии** программа Word запрашивает пароль. После успешного ввода пароля из документа удаляется **пароль на открытие** , и при открытии документа пароль больше не будет требоваться. Если требуется, чтобы документ в решении затребовал пароль, прежде чем его можно будет открыть, необходимо включить **пароль в открытом** виде после окончательной сборки и перед развертыванием решения.

## <a name="see-also"></a>См. также раздел
- [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md)
- [Обзор управления правами на информацию и расширений управляемого кода](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Как разрешите выполнение кода для документов с ограниченными разрешениями](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
