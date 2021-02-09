---
title: Практические руководства. Подписывание решений Office
description: Узнайте, как предоставить доверие Microsoft Officeному решению с помощью сертификата в качестве свидетельства.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3135962c8476fdb6970fc137e689c638299f8f81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927643"
---
# <a name="how-to-sign-office-solutions"></a>Практические руководства. Подписывание решений Office
  При подписании решения можно предоставить доверие для решения, используя сертификат в качестве свидетельства. Один и тот же сертификат можно использовать для нескольких решений, и все решения будут доверенными без дополнительных обновлений политики безопасности.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Если вы вручную изменяете манифесты приложения и развертывания с помощью Инструмент создания и изменения манифестов (*mage.exe* и *mageui.exe*), необходимо повторно подписать манифесты, прежде чем их можно будет использовать. Дополнительные сведения см. [в разделе как повторно подписывать манифесты приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="sign-by-using-a-certificate"></a>Подписывать с помощью сертификата
 Сертификат — это файл, содержащий уникальный ключ и идентификатор издателя решения. Вы можете приобрести сертификаты из центра сертификации или создать свой собственный сертификат и подписать его в центре сертификации.

 Visual Studio подписывает решения Office с временным сертификатом, чтобы включить отладку. Не следует использовать временный сертификат в развернутых решениях в качестве свидетельства.

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Подписание решения Office с помощью сертификата

1. В меню **проект** выберите **Свойства** _имя_решения_.

2. Откройте вкладку **Подписание** .

3. Выберите **подписать манифесты ClickOnce**.

4. Найдите сертификат, щелкнув **выбрать из хранилища** или **выбрав файл** и перейдя к сертификату.

5. Чтобы проверить, используется ли правильный сертификат, щелкните **Дополнительные сведения** , чтобы просмотреть сведения о сертификате.

## <a name="see-also"></a>См. также раздел

- [Безопасные решения Office](../vsto/securing-office-solutions.md)
- [Предоставление доверия решениям Office](../vsto/granting-trust-to-office-solutions.md)
- [Страница "Подписывание" в конструкторе проектов](../ide/reference/signing-page-project-designer.md)
