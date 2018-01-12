---
title: "Предоставление доверия решениям Office с помощью списков включения | Документы Microsoft"
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
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1fd73ddef389ba1f97aed46a41e1e6972135fd21
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="trusting-office-solutions-by-using-inclusion-lists"></a>Предоставление доверия решениям Office с помощью списков включения
  С помощью списков включений пользователи могут предоставлять доверие решениям Office, подписанным сертификатом, который идентифицирует издателя. Списки включений зависят от конкретного пользователя, и они могут использоваться для настроек уровня документа и надстроек VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Когда пользователь запускает решение Office, которому не было предоставлено доверие, решение Microsoft Office предлагает этому пользователю принять решение, влияющее на безопасность, в виде запроса о доверии [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Если пользователь решает доверять этому решению, настройка запускается, и в следующий раз пользователю не будет выдаваться запрос о доверии.  
  
## <a name="inclusion-list-and-windows-installer"></a>Список включений и установщик Windows  
 Для установки решений Office в каталог Program Files с помощью установщика Windows требуются права администратора. Для решений Office в каталоге Program Files Visual Studio Tools для Office среда выполнения больше не проверяет список включений, так как решениям Office уже предоставлено разрешение FullTrust.  
  
## <a name="clickonce-trust-prompt"></a>Запрос о доверии ClickOnce  
 С помощью реализации [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] для решений Office администраторы могут настроить уровень запроса о доверии, чтобы разрешить запрос, отключить запрос или требовать надежный сертификат. Эта настройка выполняется с помощью раздела реестра, который управляет доступом к списку включений.  
  
 Если запросы отключены, можно устанавливать только решения, имеющие надежный и известный сертификат. Если для уровня запросов установлено требование Authenticode, решение должно быть подписано сертификатом из известного центра, но сертификат, связанный с доверенным корневым центром (доверенный сертификат), не требуется. Если запрос разрешен, решение может быть подписано сертификатом с неизвестным удостоверением. В этом случае решение о доверии перекладывается на конечного пользователя, и для установки решения будет достаточно временного сертификата.  
  
 Дополнительные сведения см. в разделе [How to: Configure Inclusion List Security](../vsto/how-to-configure-inclusion-list-security.md) и в таблице 2 с именем "Результаты извлечения значения раздела реестра уровня запроса" в разделе [Настройка надежных издателей ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="structure-of-the-inclusion-list"></a>Структура списка включений  
 Правильная запись в списке включений состоит из двух частей: пути к манифесту развертывания и открытого ключа, используемого для подписи решения. После добавления решения в список включений оно считается доверенным. При запуске решения Office приложение Office сравнивает открытый ключ в списке включений с ключом подписывания в манифесте развертывания для проверки, что запущенное решение совпадает с исходной доверенной версией.  
  
## <a name="see-also"></a>См. также  
 [Присвоение уровня доверия решениям Office](../vsto/granting-trust-to-office-solutions.md)   
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)  
  
  