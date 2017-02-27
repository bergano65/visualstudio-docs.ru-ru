---
title: "Элемент &lt;RelatedProducts&gt; (загрузчик) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.MissingDependency"
  - "MSBuild.GenerateBootstrapper.DuplicateItems"
  - "MSBuild.GenerateBootstrapper.IncludedProductIncluded"
  - "MSBuild.GenerateBootstrapper.DependencyNotFound"
  - "MSBuild.GenerateBootstrapper.PackageFileNotFound"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<RelatedProducts> - элемент [загрузчик]"
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# Элемент &lt;RelatedProducts&gt; (загрузчик)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Элемент `RelatedProducts` определяет другие продукты, которые либо зависят от текущего продукта, либо включены в него.  
  
## Синтаксис  
  
```  
<RelatedProducts>  
    <DependsOnProduct  
        Code  
    />  
    <EitherProducts>  
        <DependsOnProduct  
            Code  
        />  
    </EitherProducts>  
    <IncludesProduct  
        Code  
    />  
</RelatedProducts>  
```  
  
## Элементы и атрибуты  
 Элемент `RelatedProducts` является дочерним для элемента `Product`.  В нем нет атрибутов.  
  
## DependsOnProduct  
 Элемент `DependsOnProduct` указывает на то, что текущий продукт зависит от именованного продукта, который должен быть установлен до установки текущего продукта.  Он является дочерним элементом элемента `RelatedProducts`.  В элементе `RelatedProducts` может содержаться как минимум один элемент `DependsOnProduct`.  
  
 Элемент `DependsOnProduct` имеет следующий атрибут.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Code`|Кодовое имя включенного продукта, заданное атрибутом `ProductCode` элемента `Product`.  Дополнительные сведения см. в разделе [Элемент \<Product\>](../deployment/product-element-bootstrapper.md).|  
  
## EitherProducts  
 Элемент `EitherProducts` определяет 0 или более элементов `DependsOnProduct` и не имеет атрибутов.  Перед текущим продуктом необходимо установить минимум один элемент `DependsOnProduct` из набора.  В элементе `RelatedProducts` может содержаться 0 или более элементов `EitherProducts`.  
  
## IncludesProduct  
 Элемент `IncludesProduct` указывает на то, что продукт включен в текущую установку и не требует отдельной установки.  Он является дочерним элементом элемента `RelatedProducts`.  В элементе `RelatedProducts` может содержаться как минимум один элемент `IncludesProduct`.  
  
 Элемент `IncludesProduct` имеет следующий атрибут.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Code`|Кодовое имя включенного продукта, заданное атрибутом `ProductCode` элемента `Product`.  Дополнительные сведения см. в разделе [Элемент \<Product\>](../deployment/product-element-bootstrapper.md).|  
  
## Пример  
 В следующем примере кода показано, что установщик Microsoft устанавливается с [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] и поэтому не требует отдельной установки.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## См. также  
 [Элемент \<Product\>](../deployment/product-element-bootstrapper.md)