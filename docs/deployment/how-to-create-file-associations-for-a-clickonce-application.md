---
title: Практическое руководство. Создание ассоциаций файлов для приложения ClickOnce | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0526351d2b3e2c223aacbe0e58d9ee39bd1b19c4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68924560"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Практическое руководство. создать ассоциацию файлов для приложения ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]приложения могут быть связаны с одним или несколькими расширениями имен файлов, чтобы приложение автоматически запускалось, когда пользователь открывает файл этих типов. Добавление в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение поддержки расширений имен файлов осуществляется просто.

### <a name="to-create-file-associations-for-a-clickonce-application"></a>Создание сопоставлений файлов для приложения ClickOnce

1. Создайте приложение в обычном режиме или используйте существующее [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]

2. Откройте манифест приложения в текстовом или XML-редакторе, например в блокноте.

3. Найдите элемент `assembly` . Дополнительные сведения см. в разделе [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md).

4. Добавьте элемент в качестве дочернего `assembly` элемента. `fileAssociation` `fileAssociation` Элемент имеет четыре атрибута:

   - `extension`: Расширение имени файла, которое необходимо связать с приложением.

   - `description`: Описание типа файла, которое будет отображаться в оболочке Windows.

   - `progid`: Строка, уникально идентифицирующая тип файла для пометки в реестре.

   - `defaultIcon`: Значок, используемый для этого типа файлов. Значок должен быть добавлен в манифест приложения как файловый ресурс. Дополнительные сведения см. в разделе [Практическое руководство. включить файл данных в приложение ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

     Пример элементов и `fileAssociation` см. `file` в разделе [ \<филеассоЦиатион > Element](../deployment/fileassociation-element-clickonce-application.md).

5. Если требуется связать с приложением более одного типа файлов, добавьте дополнительные `fileAssociation` элементы. Обратите внимание `progid` , что атрибут должен быть разным для каждого из них.

6. Завершив работу с манифестом приложения, повторно подпишите манифест. Это можно сделать из командной строки с помощью *Mage. exe*.

    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`

    Дополнительные сведения см. в разделе [Mage.exe (средство создания и редактирования манифеста)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="see-also"></a>См. также
- [\<Элемент > ФилеассоЦиатион](../deployment/fileassociation-element-clickonce-application.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
- [Mage.exe (средство создания и редактирования манифеста)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)