---
title: Включение файла данных в приложение ClickOnce
description: Узнайте, как добавить файл данных любого типа в приложение ClickOnce для сохранения в каталоге данных на локальном диске конечного компьютера.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4f4b5e8fe9d17a6de9abac2681074dcfc162e9b7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900601"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Практическое руководство. Включение файла данных в приложение ClickOnce
Каждому [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] устанавливаемому приложению назначается каталог данных на локальном диске конечного компьютера, где приложение может управлять собственными данными. Файлы данных могут включать файлы любого типа: текстовые файлы, XML-файлы или даже файлы базы данных Microsoft Access (*MDB*). В следующих процедурах показано, как добавить в приложение файл данных любого типа [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

### <a name="to-include-a-data-file-by-using-mageexe"></a>Включение файла данных с помощью Mage.exe

1. Добавьте файл данных в каталог приложения с остальными файлами приложения.

    Как правило, каталог приложения будет каталогом, помеченным текущей версией развертывания, например, v 1.0.0.0.

2. Обновите манифест приложения, чтобы получить список файлов данных.

    `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`

    При выполнении этой задачи повторно создается список файлов в манифесте приложения, а также автоматически создаются хэш-подписи.

3. Откройте манифест приложения в предпочтительном текстовом или XML-редакторе и найдите `file` элемент для недавно добавленного файла.

    Если вы добавили XML-файл с именем `Data.xml` , он будет выглядеть примерно так, как показано в следующем примере кода.

   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

4. Добавьте атрибут `type` к этому элементу и укажите для него значение `data` .

   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

5. Повторно подпишите манифест приложения с помощью пары ключей или сертификата, а затем повторно подпишите манифест развертывания.

    Необходимо повторно подписать манифест развертывания, так как его хэш манифеста приложения изменился.

    `mage -s app manifest -cf cert_file -pwd password`

    `mage -u deployment manifest -appm app manifest`

    `mage -s deployment manifest -cf certfile -pwd password`

### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Включение файла данных с помощью MageUI.exe

1. Добавьте файл данных в каталог приложения с остальными файлами приложения.

2. Как правило, каталог приложения будет каталогом, помеченным текущей версией развертывания, например, v 1.0.0.0.

3. В меню **файл** выберите команду **Открыть** , чтобы открыть манифест приложения.

4. Перейдите на вкладку **файлы** .

5. В текстовом поле в верхней части вкладки введите каталог, содержащий файлы приложения, а затем нажмите кнопку **заполнить**.

     Файл данных появится в сетке.

6. Установите для файла данных значение **типа** **данных**.

7. Сохраните манифест приложения, а затем повторно подпишите его.

     *MageUI.exe* предложит повторно подписать файл.

8. Повторно подписать манифест развертывания

     Необходимо повторно подписать манифест развертывания, так как его хэш манифеста приложения изменился.

## <a name="see-also"></a>См. также раздел
- [Доступ к локальным и удаленным данным в приложениях ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)