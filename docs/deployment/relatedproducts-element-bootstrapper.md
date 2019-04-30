---
title: '&lt;RelatedProducts&gt; элемент (загрузчик) | Документация Майкрософт'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f45b8c07cf03dc83969c3500c80b8ee215e3ad69
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62898728"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; элемент (установщик)
`RelatedProducts` Элемент определяет другие продукты, которые зависят от или включены в текущий продукт.

## <a name="syntax"></a>Синтаксис

```xml
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
 `RelatedProducts` Элемент является дочерним элементом `Product` элемент. Он не имеет атрибутов.

## <a name="dependsonproduct"></a>DependsOnProduct
 `DependsOnProduct` Элемент указывает, что текущий продукт зависит от данного продукта, и что данного продукта должно быть установлено перед текущим объектом. Он является дочерним элементом `RelatedProducts` элемент. Объект `RelatedProducts` элемент может иметь один или несколько `DependsOnProduct` элементов.

 `DependsOnProduct` содержит следующий атрибут.

|Атрибут|Описание|
|---------------|-----------------|
|`Code`|Кодовое имя включенного продукта, в соответствии с `ProductCode` атрибут `Product` элемента. Дополнительные сведения см. в разделе [ \<продукта > элемент](../deployment/product-element-bootstrapper.md).|

## <a name="eitherproducts"></a>EitherProducts
 `EitherProducts` Элемент определяет ноль или более `DependsOnProduct` элементов, и не имеет атрибутов. По крайней мере один `DependsOnProduct` в рамках этого курса необходимо установить перед текущего продукта. Объект `RelatedProducts` элемент может иметь ноль или более `EitherProducts` элементов.

## <a name="includesproduct"></a>IncludesProduct
 `IncludesProduct` Элемент указывает, что продукт входит в состав текущей установки и не требует отдельной установки. Он является дочерним элементом `RelatedProducts` элемент. Объект `RelatedProducts` элемент может иметь один или несколько `IncludesProduct` элементов.

 `IncludesProduct` содержит следующий атрибут.

|Атрибут|Описание|
|---------------|-----------------|
|`Code`|Кодовое имя включенного продукта, в соответствии с `ProductCode` атрибут `Product` элемента. Дополнительные сведения см. в разделе [ \<продукта > элемент](../deployment/product-element-bootstrapper.md).|

## <a name="example"></a>Пример
 В следующем примере кода указывает, что установщик Microsoft устанавливается вместе с [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]и поэтому не требует отдельной установки.

```xml
<RelatedProducts>
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
</RelatedProducts>
```

## <a name="see-also"></a>См. также
- [\<Продукт > элемент](../deployment/product-element-bootstrapper.md)