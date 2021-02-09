---
title: '&lt;&gt;элемент филеассоЦиатион (приложение ClickOnce) | Документация Майкрософт'
description: Элемент ФилеассоЦиатион определяет расширение файла, связываемое с приложением. Элемент ФилеассоЦиатион является необязательным.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7435a4e4973ee0a000555e9508328a76f7aa59a6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889152"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;&gt;элемент филеассоЦиатион (приложение ClickOnce)
Определяет расширение файла, связываемое с приложением.

## <a name="syntax"></a>Синтаксис

```xml
<fileAssociation
    xmlns="urn:schemas-microsoft-com:clickonce.v1"
    extension
    description
    progid
    defaultIcon
/>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `fileAssociation` является необязательным. Элемент имеет перечисленные ниже атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|`extension`|Обязательный элемент. Расширение файла, связываемое с приложением.|
|`description`|Обязательный элемент. Описание типа файла для использования оболочкой.|
|`progid`|Обязательный элемент. Имя, уникально идентифицирующее тип файла.|
|`defaultIcon`|Обязательный элемент. Указывает значок, используемый для файлов с этим расширением. Файл значка необходимо указать с помощью [ \<file> элемента](../deployment/file-element-clickonce-application.md) в [ \<assembly> элементе](../deployment/assembly-element-clickonce-application.md) , который содержит этот элемент.|

## <a name="remarks"></a>Remarks
 Этот элемент должен включать ссылку на пространство имен XML в "urn: schemas-microsoft-com: ClickOnce. v1". Если `<fileAssociation>` элемент используется, он должен находиться после `<application>` элемента в его родительском [ \<assembly> элементе](../deployment/assembly-element-clickonce-application.md).

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] не будет перезаписывать существующие сопоставления файлов. Однако приложение ClickOnce может переопределить расширение файла только для текущего пользователя. После удаления этого приложения ClickOnce служба ClickOnce удаляет сопоставление файлов для пользователя, а связь для каждого компьютера снова становится активной.

## <a name="example"></a>Пример
 В следующем примере кода показаны `fileAssociation` элементы манифеста приложения для приложения текстового редактора, развернутого с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Этот пример кода также включает [ \<file> элемент](../deployment/file-element-clickonce-application.md) , необходимый для `defaultIcon` атрибута.

```xml
<file name="text.ico" size="4286">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>
  </hash>
</file>
<file name="writing.ico" size="9662">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>
  </hash>
</file>
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />
```

## <a name="see-also"></a>См. также раздел
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)