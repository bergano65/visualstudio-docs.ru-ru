---
title: '&lt;&gt;Элемент релатедпродуктс (начальный загрузчик) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70afe724be5b782bc90e162fd65f83ad1b0d0d23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202534"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;&gt;Элемент релатедпродуктс (начальный загрузчик)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`RelatedProducts`Элемент определяет другие продукты, которые либо зависят от, либо включены в текущий продукт.  
  
## <a name="syntax"></a>Синтаксис  
  
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
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `RelatedProducts`Элемент является дочерним по отношению к `Product` элементу. У него нет атрибутов.  
  
## <a name="dependsonproduct"></a>депендсонпродукт  
 `DependsOnProduct`Элемент означает, что текущий продукт зависит от именованного продукта и что именованный продукт должен быть установлен перед текущим. Это дочерний `RelatedProducts` элемент элемента. `RelatedProducts`Элемент может иметь один или несколько `DependsOnProduct` элементов.  
  
 `DependsOnProduct` имеет следующий атрибут.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Code`|Кодовое имя включаемого продукта, как указано в `ProductCode` атрибуте `Product` элемента. Дополнительные сведения см. в разделе [\<Product>Element](../deployment/product-element-bootstrapper.md).|  
  
## <a name="eitherproducts"></a>еисерпродуктс  
 `EitherProducts`Элемент определяет ноль или более `DependsOnProduct` элементов и не имеет атрибутов. По крайней мере один `DependsOnProduct` из этих наборов должен быть установлен до текущего продукта. `RelatedProducts`Элемент может иметь ноль или более `EitherProducts` элементов.  
  
## <a name="includesproduct"></a>инклудеспродукт  
 `IncludesProduct`Элемент означает, что продукт включен в текущую установку и не требует отдельной установки. Это дочерний `RelatedProducts` элемент элемента. `RelatedProducts`Элемент может иметь один или несколько `IncludesProduct` элементов.  
  
 `IncludesProduct` имеет следующий атрибут.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Code`|Кодовое имя включаемого продукта, как указано в `ProductCode` атрибуте `Product` элемента. Дополнительные сведения см. в разделе [\<Product>Element](../deployment/product-element-bootstrapper.md).|  
  
## <a name="example"></a>Пример  
 В следующем примере кода указывается, что установщик Microsoft устанавливается вместе с [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , и поэтому не требуется отдельная установка.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>См. также:  
 [\<Product> Элемент](../deployment/product-element-bootstrapper.md)
