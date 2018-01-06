---
title: "&lt;fileAssociation&gt; элемент (приложение ClickOnce) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: "8"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: bd5d7ed1a37923cefc4a6b7975610b6016fd0ae6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileAssociation&gt; элемент (приложение ClickOnce)
Определяет расширение файла, нужно связать с приложением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Элемент `fileAssociation` является необязательным. Элемент имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`extension`|Обязательно. Расширение файла, который нужно связать с приложением.|  
|`description`|Обязательно. Описание типа файла для использования в оболочке.|  
|`progid`|Обязательно. Имя, однозначно определяющее тип файла.|  
|`defaultIcon`|Обязательно. Указывает значок, используемый для файлов с расширением. Файл значка должен быть указан с помощью [ \<файл > элемент](../deployment/file-element-clickonce-application.md) в [ \<сборки > элемент](../deployment/assembly-element-clickonce-application.md) , содержащий этот элемент.|  
  
## <a name="remarks"></a>Примечания  
 Этот элемент должен включать ссылки на пространство имен XML в «urn: schemas-microsoft-com:clickonce.v1». Если `<fileAssociation>` элемент используется, он должен следовать после `<application>` элемента в его родительском [ \<сборки > элемент](../deployment/assembly-element-clickonce-application.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]не перезаписывает существующие сопоставления файлов. Тем не менее приложения ClickOnce можно переопределить расширение файла для только для текущего пользователя. После удаления этого приложения ClickOnce, ClickOnce удалит сопоставления файлов для пользователя и ассоциации для компьютера active.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан `fileAssociation` элементы в приложении манифеста для приложение текстового редактора, развернутые с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Этот пример кода также включает [ \<файл > элемент](../deployment/file-element-clickonce-application.md) за счет `defaultIcon` атрибута.  
  
```  
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
  
## <a name="see-also"></a>См. также  
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)