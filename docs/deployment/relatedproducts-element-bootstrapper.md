---
title: '&lt;&gt;Элемент релатедпродуктс (начальный загрузчик) | Документация Майкрософт'
description: Элемент Релатедпродуктс определяет другие продукты, которые либо зависят от текущего продукта, либо включены в него.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a7987306d9f7fc25f9f9b783d5b0966ac5015ce0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949692"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;&gt;Элемент релатедпродуктс (начальный загрузчик)
`RelatedProducts`Элемент определяет другие продукты, которые либо зависят от, либо включены в текущий продукт.

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
 В следующем примере кода указывается, что установщик Microsoft устанавливается вместе с платформа .NET Framework и поэтому не требует отдельной установки.

```xml
<RelatedProducts>
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
</RelatedProducts>
```

## <a name="see-also"></a>См. также раздел
- [Элемент \<Product>](../deployment/product-element-bootstrapper.md)