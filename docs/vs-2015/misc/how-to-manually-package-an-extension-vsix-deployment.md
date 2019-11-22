---
title: 'How to: Manually Package an Extension (VSIX Deployment) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: d25990e0-e782-4a79-9d9a-1caf3c56c6a2
caps.latest.revision: 10
manager: jillfra
ms.openlocfilehash: a615aea75ec00e49ee4d2837b8b4e2b1d20d3306
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293621"
---
# <a name="how-to-manually-package-an-extension-vsix-deployment"></a>Практическое руководство. Упаковка расширения (развертывания VSIX) вручную
Вы можете создать пакет VSIX для инкапсуляции расширения [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для развертывания. Создать пакет можно тремя способами.  
  
- Создайте проект пакета VSIX с помощью одного из шаблонов расширяемости, которые включены в пакет SDK для [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . В большинстве ситуаций это самый простой вариант.  
  
- Поместите выходные данные проекта расширения в пустой [проект VSIX](../extensibility/vsix-project-template.md). Мы рекомендуем использовать этот вариант для шаблонов, неподдерживаемых сборок и пользовательских типов.  
  
- Создайте пакет VSIX вручную. Этот вариант рекомендуется только в том случае, если использовать другие два варианта невозможно.  
  
  В этом документе описывается третий вариант.  
  
## <a name="creating-a-vsix-package"></a>Создание пакета VSIX  
 Чтобы вручную упаковать расширение, добавьте файлы extension.manifest и [Content_Types].xml в проект расширения, поместите их в сжатый файл вместе с выходными данными сборки и переименуйте сжатый файл так, чтобы он имел расширение VSIX. Упаковываемое расширения должно иметь тип, поддерживаемый [схемой VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
> [!NOTE]
> The names of files in VSIX packages must not include spaces, nor characters that are reserved in Uniform Resource Identifiers (URI), as defined under [\[RFC2396\]](https://go.microsoft.com/fwlink/?LinkId=90339).  
  
#### <a name="to-manually-create-a-vsix-package"></a>Создание пакета VSIX вручную  
  
1. Создайте расширение Visual Studio типа, поддерживаемого схемой VSIX.  
  
2. Создайте XML-файл и назовите его `extension.vsixmanifest`.  
  
3. Заполните файл extension.vsixmanifest в соответствии со схемой VSIX. Пример манифеста см. в разделе [Элемент PackageManifest (корневой элемент, схема VSX)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
4. Создайте еще один XML-файл и назовите его `[Content_Types].xml`.  
  
5. Fill in the [Content_Types].xml file as specified in [The Structure of the Content_types\].xml File](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
6. Поместите оба XML-файла в один каталог с развертываемым расширением.  
  
     В случае с шаблоном проекта или шаблоном элемента поместите ZIP-файл, который содержит шаблон, в ту же папку, что и XML-файлы. Не помещайте XML-файлы в ZIP-файл.  
  
     Во всех остальных случаях поместите XML-файлы в тот же каталог, что и выходные данные сборки.  
  
7. В проводнике щелкните правой кнопкой мыши папку, содержащую расширение и два XML-файла, выберите пункт **Отправить**, а затем пункт **Сжатая ZIP-папка**.  
  
8. Переименуйте полученный ZIP-файл в *Имя_файла*.vsix, где *Имя_файла* — это имя распространяемого файла, устанавливающего пакет.  
  
## <a name="see-also"></a>См. также раздел  
 [Shipping Visual Studio Extensions](../extensibility/shipping-visual-studio-extensions.md)   
 [Anatomy of a VSIX Package](../extensibility/anatomy-of-a-vsix-package.md)   
 [PackageManifest Element (Root Element, VSX Schema)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187)