---
title: Решения SharePoint. Создание пользовательских функций, пакета правил проверки
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a10118a0c83f9e17e32efd293a9a824e38a0942a
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835928"
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>Практическое руководство. Создание пользовательских компонентов и пакетов правила проверки для решений SharePoint
  Можно создать пользовательские правила проверки для проверки пакета решения, созданные Visual Studio. Можно выполнить полную проверку на весь компонент или пакет, выбрав **Validate** в контекстном меню, пакета или компонента в **PackagingExplorer**. Частичная проверка выполняется при добавлении новой функции или элементов проекта SharePoint в проект, чтобы определить, пакета или компонента будет находиться в допустимом состоянии.

### <a name="to-create-a-custom-package-validation-rule"></a>Чтобы создать настраиваемое правило проверки пакета

1. Создайте проект библиотеки классов.

2. Добавьте ссылки на следующие сборки:

    - Microsoft.VisualStudio.SharePoint

    - System.ComponentModel.Composition

3. Создайте класс, который реализует один из следующих интерфейсов:

    - Чтобы создать правило проверки пакета, реализуйте <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> интерфейс.

    - Чтобы создать правило проверки компонента, реализуйте <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> интерфейс.

4. Добавить <xref:System.ComponentModel.Composition.ExportAttribute> к классу. Этот атрибут позволяет Visual Studio для обнаружения и загрузки правил проверки. Передайте <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> или <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> тип конструктору атрибута.

## <a name="example"></a>Пример
 В следующем примере кода показано, как создать пользовательское правило проверки компонента.

 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]

## <a name="compile-the-code"></a>Компиляция кода
 В этом примере требуются ссылки на следующие сборки:

- Microsoft.VisualStudio.SharePoint.

- System.ComponentModel.Composition.

## <a name="deploy-the-extension"></a>Развертывание расширения
 Чтобы развернуть расширение, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [средства развертывания расширений для SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также
- [Расширение SharePoint упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
