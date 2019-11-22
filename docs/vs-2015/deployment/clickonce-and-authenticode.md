---
title: ClickOnce and Authenticode | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- .pfx files
- ClickOnce deployment, Authenticode
- Authenticode, ClickOnce
- ClickOnce deployment, certificates
- ClickOnce deployment, security
ms.assetid: ab5b6712-f32a-4e33-842f-e88ab4818ccf
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 06edf9954134a6110f9285fc744c87c2696b19d5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298270"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce и технология Authenticode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Authenticode* is a Microsoft technology that uses industry-standard cryptography to sign application code with digital certificates that verify the authenticity of the application's publisher. Используя Authenticode для развертывания приложения, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] снижает риск заражения программой-трояном. Программа-троян — это вирус или другая вредоносная программа, которые злоумышленник представляет как легальную программу, исходящую из авторитетного и заслуживающего доверия источника. Подписание развертываний [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] с помощью цифрового сертификата — это необязательный шаг, позволяющий убедиться, что сборки и файлы не были изменены.  
  
 В следующих разделах описываются различные типы цифровых сертификатов, используемых в Authenticode, способ проверки сертификатов с помощью центров сертификации (ЦС), роль меток времени в сертификатах и методы хранения сертификатов.  
  
## <a name="authenticode-and-code-signing"></a>Authenticode и подписывание кода  
 *Цифровой сертификат* — это файл, содержащий пару из открытого и закрытого криптографических ключей вместе с метаданными, описывающими издателя, которому был выдан сертификат, и агентство, выдавшее сертификат.  
  
 Существуют различные типы сертификатов Authenticode. Каждый из них настроен для разных типов подписывания. Для приложений [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] требуется сертификат Authenticode, пригодный для подписания кода. Если попытаться войти приложение [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] с помощью другого типа сертификата, например цифрового сертификата электронной почты, он не будет работать. Дополнительные сведения см. в разделе [Знакомство с подписыванием кода](https://go.microsoft.com/fwlink/?LinkId=179452).  
  
 Сертификат для подписывания кода можно получить одним из трех способов:  
  
- приобрести у поставщика сертификатов;  
  
- получить от группы, которая отвечает за создание цифровых сертификатов в вашей организации.  
  
- создать собственный с помощью MakeCert.exe, который входит в состав [!INCLUDE[winsdklong](../includes/winsdklong-md.md)].  
  
### <a name="how-using-certificate-authorities-helps-users"></a>Польза центров сертификации для пользователей  
 A certificate generated using the MakeCert.exe utility is commonly called a *self-cert* or a *test cert*. This kind of certificate works much the same way that a .snk file works in the .NET Framework. Он состоит только из пары открытого и закрытого криптографических ключей и не содержит проверяемых сведений об издателе. Автосертификаты можно использовать для развертывания приложений [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] с высоким уровнем доверия в интрасети. Однако когда эти приложения выполняются на клиентском компьютере, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] идентифицирует их как поступающие от неизвестного издателя. По умолчанию приложения [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , подписанные с помощью автосертификатов и развертываемые через Интернет, не могут использовать развертывание доверенных приложений.  
  
 И наоборот, если вы получаете сертификат из такого центра сертификации, как поставщик сертификатов или отдел внутри вашей организации, этот сертификат обеспечивает повышенную безопасность для пользователей. Он не только идентифицирует издателя подписанного программного обеспечения, но и проверяет его удостоверение путем сверки с ЦС, подписавшим его. Если ЦС не является корневым, Authenticode также выстраивает обратную "цепочку" до корневого центра, чтобы убедиться, что ЦС авторизован для выдачи сертификатов. Для повышения безопасности следует по возможности использовать сертификат, выданный центром сертификации.  
  
 For more information about generating self-certs, see [Makecert.exe (Certificate Creation Tool)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).  
  
### <a name="timestamps"></a>Метки времени  
 Сертификаты, используемые для подписи приложений [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , имеют определенный срок действия, который обычно составляет двенадцать месяцев. Чтобы устранить необходимость в постоянном повторном подписывании приложений с использованием новых сертификатов, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] поддерживает метку времени. Когда приложение подписано с меткой времени, его сертификат будет приниматься даже после истечения срока действия, при условии, что действительна метка времени. Это позволяет скачивать и запускать приложения [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] с просроченными сертификатами, но действительными метками времени. Кроме того, это позволяет установленным приложениям с просроченными сертификатами продолжать скачивать и устанавливать обновления.  
  
 Чтобы включить метку времени на сервер приложений, должен быть доступен сервер меток времени. Сведения о выборе сервера меток времени см. в разделе [How to: Sign Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
### <a name="updating-expired-certificates"></a>Обновление сертификатов с истекшим сроком действия  
 В более ранних версиях платформы .NET Framework обновление приложения, у которого истек срок действия сертификата, могло привести к прекращению работы этого приложения. Чтобы устранить эту проблему, воспользуйтесь одним из следующих способов:  
  
- Обновите платформу .NET Framework до версии 2.0 с пакетом обновления 1 или более поздней в Windows XP или до версии 3.5 или более поздней в Windows Vista.  
  
- Удалите приложение и переустановите новую версию с действительным сертификатом.  
  
- Создайте сборку командной строки, которая обновляет сертификат. Пошаговые инструкции для этого процесса можно найти в [справочной статье 925521 Майкрософт](https://go.microsoft.com/fwlink/?LinkId=179454).  
  
### <a name="storing-certificates"></a>Хранение сертификатов  
  
- Сертификаты можно хранить в виде PFX-файла в файловой системе или внутри контейнера ключей. Пользователь в домене Windows может иметь несколько контейнеров ключей. По умолчанию MakeCert.exe сохраняет сертификаты в личном контейнере ключей, если не указано, что сертификат должен храниться в виде PFX-файла. Mage.exe и MageUI.exe — инструменты [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] для создания развертываний [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] — позволяют использовать сертификаты, хранящиеся в любом режиме.  
  
## <a name="see-also"></a>См. также раздел  
 [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Общие сведения о развертывании доверенных приложений](../deployment/trusted-application-deployment-overview.md)   
 [Mage.exe (средство создания и редактирования манифеста)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
