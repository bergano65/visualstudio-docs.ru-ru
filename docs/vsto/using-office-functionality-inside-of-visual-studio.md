---
title: Использование функций Office в Visual Studio
description: Узнайте, как документ и связанное приложение из проекта уровня документа размещаются в Visual Studio, чтобы вы могли работать непосредственно с документом.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c93994b233990e2362c62445909adb66a0eeeb9b
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528403"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Использование функций Office в Visual Studio
  При создании проекта на уровне документа документ и связанное с ним приложение размещаются в Visual Studio, что позволяет проектировать и работать непосредственно с документом. Если в Visual Studio открыто приложение Microsoft Office, оно обычно работает правильно. Однако некоторые функциональные возможности приложения отличаются или недоступны.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>Защита документов
 Microsoft Office Word и Microsoft Office Excel предлагают функции защиты документов, которые можно использовать в проектах. Однако если защита документов включена, а документ открыт в Visual Studio, это может препятствовать внесению каких-либо изменений в структуру. Дополнительные сведения см. [в статье Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md).

## <a name="information-rights-management"></a>Управление правами на информацию
 Информация Rights Management (IRM) доступна в Microsoft Office Word и Microsoft Office Excel. IRM может помочь предотвратить несанкционированный просмотр или изменение конфиденциальной информации. Однако IRM также может препятствовать запуску кода. Дополнительные сведения см. в статье Общие сведения об [управлении правами на информацию и расширениях управляемого кода](../vsto/information-rights-management-and-managed-code-extensions-overview.md).

## <a name="password-protection"></a>Защита пароля
 Microsoft Office документы Word и Microsoft Office книги Excel можно настроить таким образом, чтобы они не были открыты пользователем, который не знает пароль. Защита паролем обрабатывается по-разному в Word и Excel и может повлиять на процесс разработки. Дополнительные сведения см. [в статье Защита паролем в документах Office](../vsto/password-protection-on-office-documents.md).

## <a name="see-also"></a>См. также раздел
- [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md)
- [Обзор управления правами на информацию и расширений управляемого кода](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Защита паролем в документах Office](../vsto/password-protection-on-office-documents.md)
- [Руководство. Открытие решений Office без выполнения кода](../vsto/how-to-open-office-solutions-without-running-code.md)
