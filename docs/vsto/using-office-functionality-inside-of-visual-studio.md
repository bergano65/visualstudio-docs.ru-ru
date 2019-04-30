---
title: Использование функциональных возможностей Office в Visual Studio
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
ms.openlocfilehash: c47ed9639a33ecdea3451c63b729d959f6855e5d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62982327"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Использование функциональных возможностей Office в Visual Studio
  При создании проекта уровня документа, документа и сопоставленного приложения размещаются в Visual Studio, чтобы можно создать и работать непосредственно с документом. Если у вас есть Microsoft Office, откройте приложение в Visual Studio, обычно работает ожидаемым образом. Тем не менее некоторые функциональные возможности приложения, могут оказаться недоступными или.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>Защита документов
 Microsoft Office Word и Microsoft Office Excel предлагают функции защиты, которые можно использовать в проектах документов. Тем не менее если защита включена, когда документ открыт в среде Visual Studio, он может препятствовать вы внесение некоторых изменений в проект. Дополнительные сведения см. в разделе [защита в решениях уровня документа документов](../vsto/document-protection-in-document-level-solutions.md).

## <a name="information-rights-management"></a>Управление правами
 Управление правами на доступ к данным (IRM) доступен в Microsoft Office Word и Microsoft Office Excel. IRM может помочь предотвратить несанкционированного просмотра и изменения конфиденциальной информации. Тем не менее IRM можно также предотвратить ваш код выполняется. Дополнительные сведения см. в разделе [Information rights management и общие сведения о расширениях управляемого кода](../vsto/information-rights-management-and-managed-code-extensions-overview.md).

## <a name="password-protection"></a>Защита паролем
 Документы Microsoft Office Word и книг Microsoft Office Excel можно задать, чтобы они не удается открыть тому, кто не знает пароль. Защита паролем обрабатывается по-разному в Word и Excel и может повлиять на процесс разработки. Дополнительные сведения см. в разделе [защита паролей в документах Office](../vsto/password-protection-on-office-documents.md).

## <a name="see-also"></a>См. также
- [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md)
- [Управление правами и общие сведения о расширениях управляемого кода](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Защита паролей в документах Office](../vsto/password-protection-on-office-documents.md)
- [Практическое руководство. Открытие решений Office без выполнения кода](../vsto/how-to-open-office-solutions-without-running-code.md)
