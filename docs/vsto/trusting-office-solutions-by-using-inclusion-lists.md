---
title: Доверия решениям Office с помощью списков включения
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9e2fea115b941af4b119b59dade16114cab3383d
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38783705"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>Доверия решениям Office с помощью списков включения
  С помощью списков включений пользователи могут предоставлять доверие решениям Office, подписанным сертификатом, который идентифицирует издателя. Списки включений зависят от конкретного пользователя, и они могут использоваться для настроек уровня документа и надстроек VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Когда пользователь запускает решение Office, которому не было предоставлено доверие, решение Microsoft Office предлагает этому пользователю принять решение, влияющее на безопасность, в виде запроса о доверии [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Если пользователь решает доверять этому решению, настройка запускается, и в следующий раз пользователю не будет выдаваться запрос о доверии.  
  
## <a name="inclusion-list-and-windows-installer"></a>Список включений и установщик Windows  
 Для установки решений Office в *Program Files* каталога с помощью установщика Windows требуются права администратора. Для решений Office в *Program Files* каталог, Visual Studio Tools для Office runtime, больше не проверяет список включений, так как решения Office уже было предоставлено разрешение FullTrust.  
  
## <a name="clickonce-trust-prompt"></a>Запрос о доверии ClickOnce  
 С помощью реализации [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] для решений Office администраторы могут настроить уровень запроса о доверии, чтобы разрешить запрос, отключить запрос или требовать надежный сертификат. Эта настройка выполняется с помощью раздела реестра, который управляет доступом к списку включений.  
  
 Если запросы отключены, можно устанавливать только решения, имеющие надежный и известный сертификат. Если для уровня запросов установлено требование Authenticode, решение должно быть подписано сертификатом из известного центра, но сертификат, связанный с доверенным корневым центром (доверенный сертификат), не требуется. Если запрос разрешен, решение может быть подписано сертификатом с неизвестным удостоверением. В этом случае решение о доверии перекладывается на конечного пользователя, и для установки решения будет достаточно временного сертификата.  
  
 Дополнительные сведения см. в разделе [как: настройка безопасности списка включения](../vsto/how-to-configure-inclusion-list-security.md) и в таблице 2, под названием запроса уровень реестра ключ значение запуска эффектов, в [ClickOnce Настройка доверенных издателей](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="structure-of-the-inclusion-list"></a>Структура списка включений  
 Правильная запись в списке включений состоит из двух частей: пути к манифесту развертывания и открытого ключа, используемого для подписи решения. После добавления решения в список включений оно считается доверенным. При запуске решения Office приложение Office сравнивает открытый ключ в списке включений с ключом подписывания в манифесте развертывания для проверки, что запущенное решение совпадает с исходной доверенной версией.  
  
## <a name="see-also"></a>См. также  
 [Предоставление доверия решениям Office](../vsto/granting-trust-to-office-solutions.md)   
 [Безопасные решения Office](../vsto/securing-office-solutions.md)  
  
  