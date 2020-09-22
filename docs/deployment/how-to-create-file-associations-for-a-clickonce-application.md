---
title: Создание сопоставлений файлов (приложение ClickOnce)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: fcca57415eae6480286f457755b996f22cb6507a
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809785"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Практическое руководство. Создание ассоциаций файлов для приложения ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения могут быть связаны с одним или несколькими расширениями имен файлов, чтобы приложение автоматически запускалось, когда пользователь открывает файл этих типов. Добавление в приложение поддержки расширений имен файлов [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] осуществляется просто.

### <a name="to-create-file-associations-for-a-clickonce-application"></a>Создание сопоставлений файлов для приложения ClickOnce

1. Создайте [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение в обычном режиме или используйте существующее [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение.

2. Откройте манифест приложения в текстовом или XML-редакторе, например в блокноте.

3. Найдите элемент `assembly` . Дополнительные сведения см. в разделе [манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md).

4. Добавьте элемент в качестве дочернего элемента `assembly` `fileAssociation` . `fileAssociation`Элемент имеет четыре атрибута:

   - `extension`: Расширение имени файла, которое необходимо связать с приложением.

   - `description`: Описание типа файла, которое будет отображаться в оболочке Windows.

   - `progid`: Строка, уникально идентифицирующая тип файла для пометки в реестре.

   - `defaultIcon`: Значок, используемый для этого типа файлов. Значок должен быть добавлен в манифест приложения как файловый ресурс. Дополнительные сведения см. в разделе [Практическое руководство. включить файл данных в приложение ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

     Пример `file` `fileAssociation` элементов и см. в разделе [ \<fileAssociation> element](../deployment/fileassociation-element-clickonce-application.md).

5. Если требуется связать с приложением более одного типа файлов, добавьте дополнительные `fileAssociation` элементы. Обратите внимание, что `progid` атрибут должен быть разным для каждого из них.

6. Завершив работу с манифестом приложения, повторно подпишите манифест. Это можно сделать из командной строки с помощью *Mage.exe*.

    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`

    Дополнительные сведения см. в разделе [Mage.exe (средство создания и редактирования манифеста)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="see-also"></a>См. также раздел
- [\<fileAssociation> дерев](../deployment/fileassociation-element-clickonce-application.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
- [Mage.exe (средство создания и редактирования манифеста)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)