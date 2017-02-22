---
title: "Элемент &lt;fileAssociation&gt; (приложение ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<fileAssociation> - элемент [манифест приложения ClickOnce]"
  - "манифесты [ClickOnce], элемент <fileAssociation>"
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Элемент &lt;fileAssociation&gt; (приложение ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определяет расширение файла, которое требуется связать с приложением.  
  
## Синтаксис  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## Элементы и атрибуты  
 Элемент `fileAssociation` является необязательным.  Элемент имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`extension`|Обязательный.  Расширение имени файла, которое требуется связать с приложением.|  
|`description`|Обязательный.  Описание типа файла, используемого оболочкой.|  
|`progid`|Обязательный.  Имя, однозначно определяющее тип файла.|  
|`defaultIcon`|Обязательный.  Задание значка, используемого для файлов с таким расширением.  Файл значка необходимо указать с помощью элемента [Элемент \<file\>](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md) в элементе [Элемент \<assembly\>](../deployment/assembly-element-clickonce-application.md), содержащем данный элемент.|  
  
## Заметки  
 Данный элемент должен включать ссылку пространства имен XML на "urn:schemas\-microsoft\-com:clickonce.v1".  Если используется элемент `<fileAssociation>`, он должен находиться после элемента `<application>` в его родительском элементе [Элемент \<assembly\>](../deployment/assembly-element-clickonce-application.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] не перезаписывает существующие сопоставления файлов.  Однако приложение ClickOnce может переопределять расширение файла только для текущего пользователя.  После удаления этого приложения ClickOnce удаляет сопоставление файлов для пользователя, и сопоставление на уровне компьютера снова становится активным.  
  
## Пример  
 В следующем примере кода показаны элементы `fileAssociation` в манифесте приложения для текстового редактора, развернутого с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Этот пример кода также включает элемент [Элемент \<file\>](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md), необходимый для атрибута `defaultIcon`.  
  
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
  
## См. также  
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)