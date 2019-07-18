---
title: Практическое руководство. Подписывание решений Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1fff7555c17f4fdac43de2690f8e133cc32881db
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62971125"
---
# <a name="how-to-sign-office-solutions"></a>Практическое руководство. Подписывание решений Office
  Если вы вошли в это решение, можно предоставить доверие, используя сертификат в качестве свидетельства. Тот же сертификат можно использовать для нескольких решений, и все решения будут доверенными без обновлений политики обеспечения дополнительной безопасности.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Если вы вручную изменить приложение и манифесты развертывания с помощью Manifest Generation and Editing Tool (*mage.exe* и *mageui.exe*), необходимо повторно подписать манифесты, прежде чем их можно использовать. Дополнительные сведения см. в разделе [Как повторно подписать манифесты приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="sign-by-using-a-certificate"></a>Войдите с помощью сертификата
 Сертификат — это файл, который содержит уникальный ключ и идентификатор издателя решения. Можно приобрести сертификаты из центра сертификации, или создать собственный сертификат и подписать его сертификации.

 Visual Studio подписывает решений Office с помощью временный сертификат для включения отладки. Не следует использовать временный сертификат в развернутых решениях в качестве свидетельства.

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Для подписи решения Office с помощью сертификата

1. На **проекта** меню, щелкните _SolutionName_**свойства**.

2. Откройте вкладку **Подписывание**.

3. Выберите **подписать манифесты ClickOnce**.

4. Найдите сертификат, нажав кнопку **выберите Store** или **выбрать из файла** и переход к сертификату.

5. Чтобы убедиться, что используется правильный сертификат, нажмите кнопку **Подробнее** для просмотра сведений о сертификате.

## <a name="see-also"></a>См. также

- [Безопасные решения Office](../vsto/securing-office-solutions.md)
- [Предоставление доверия решениям Office](../vsto/granting-trust-to-office-solutions.md)
- [Страница "Подписывание" в конструкторе проектов](../ide/reference/signing-page-project-designer.md)
