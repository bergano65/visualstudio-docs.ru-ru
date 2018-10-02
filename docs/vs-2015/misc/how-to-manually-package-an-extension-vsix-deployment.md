---
title: 'Практическое: упаковка расширения (развертывания VSIX) вручную | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d25990e0-e782-4a79-9d9a-1caf3c56c6a2
caps.latest.revision: 10
manager: douge
ms.openlocfilehash: 16803e9019928da5676850899025b190df08a30a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558912"
---
# <a name="how-to-manually-package-an-extension-vsix-deployment"></a>Практическое руководство. Упаковка расширения (развертывания VSIX) вручную
Можно создать пакет VSIX для инкапсуляции [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] расширения для развертывания. Создать пакет можно тремя способами.  
  
-   Создайте проект пакета VSIX с помощью одного из шаблонов расширяемости, которые включены в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] пакета SDK. В большинстве ситуаций это самый простой вариант.  
  
-   Поместите выходные данные проекта расширения в пустой [проект VSIX](../extensibility/vsix-project-template.md). Мы рекомендуем использовать этот вариант для шаблонов, неподдерживаемых сборок и пользовательских типов.  
  
-   Создайте пакет VSIX вручную. Этот вариант рекомендуется только в том случае, если использовать другие два варианта невозможно.  
  
 В этом документе описывается третий вариант.  
  
## <a name="creating-a-vsix-package"></a>Создание пакета VSIX  
 Чтобы вручную упаковать расширение, добавьте файлы extension.manifest и [Content_Types].xml в проект расширения, поместите их в сжатый файл вместе с выходными данными сборки и переименуйте сжатый файл так, чтобы он имел расширение VSIX. Упаковываемое расширения должно иметь тип, поддерживаемый [схемой VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
> [!NOTE]
>  Имена файлов в пакетах VSIX не должны содержать пробелы, а также символы, которые зарезервированы в универсальных кодов ресурса (URI), как определенные в разделе [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
#### <a name="to-manually-create-a-vsix-package"></a>Создание пакета VSIX вручную  
  
1.  Создайте расширение Visual Studio типа, поддерживаемого схемой VSIX.  
  
2.  Создайте XML-файл и назовите его `extension.vsixmanifest`.  
  
3.  Заполните файл extension.vsixmanifest в соответствии со схемой VSIX. Пример манифеста см. в разделе [элемент PackageManifest (корневой элемент, Схема VSX)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
4.  Создайте еще один XML-файл и назовите его `[Content_Types].xml`.  
  
5.  Заполните файл [Content_Types] .xml, как указано в [структура Content_types\].xml файл](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
6.  Поместите оба XML-файла в один каталог с развертываемым расширением.  
  
     В случае с шаблоном проекта или шаблоном элемента поместите ZIP-файл, который содержит шаблон, в ту же папку, что и XML-файлы. Не помещайте XML-файлы в ZIP-файл.  
  
     Во всех остальных случаях поместите XML-файлы в тот же каталог, что и выходные данные сборки.  
  
7.  В проводнике щелкните правой кнопкой мыши папку, содержащую расширение и два XML-файла, выберите пункт **Отправить**, а затем пункт **Сжатая ZIP-папка**.  
  
8.  Переименуйте полученный ZIP-файл в *Имя_файла*.vsix, где *Имя_файла* — это имя распространяемого файла, устанавливающего пакет.  
  
## <a name="see-also"></a>См. также  
 [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Элемент PackageManifest (корневой элемент, Схема VSX)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187)