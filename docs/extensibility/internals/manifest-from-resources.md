---
title: Манифест из ресурсов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d35f8486ae85f0933d30b9587f2fc59652071a85
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56626730"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
Консольное приложение, которое принимает список ресурсов изображений (PNG- или .xaml-файлы) и создает файл .imagemanifest, который позволяет этих образов для использования в службе Visual Studio изображение является манифест из ресурсов средства. Кроме того это средство можно использовать для добавления картинок в существующих .imagemanifest. Это средство можно использовать для добавления поддержку высокого DPI и темы для изображений в расширение Visual Studio. Следует включены в файле созданный .imagemanifest и развернут как часть расширений Visual Studio (VSIX).

## <a name="how-to-use-the-tool"></a>Как использовать средство
 **Синтаксис**

 ManifestFromResources /resources:\<Dir1 >;\< Img1 >/Assembly:\<AssemblyName > \<необязательные аргументы >

 **Аргументы**

||||
|-|-|-|
|**Имя коммутатора**|**Примечания**|**Обязательный или необязательный**|
|/Resources|Разделенный точками с запятой список изображений или каталоги. Этот список всегда должен содержать полный список образов, которые будут в манифесте. Если только список неполный, не включены операции будут потеряны.<br /><br /> Если файла определенного ресурса — это группа изображений, средство будет разбить на отдельные образы перед добавлением каждого subimage в манифест.<br /><br /> Если изображение PNG-файл, мы рекомендуем форматировать имя вот так, чтобы средство можно заполнить необходимыми атрибутами для образа: \<Имя >. \<Ширины >. \<Высота > .png.|Обязательно|
|/ Assembly|Имя управляемой сборки (без расширения), или путь выполнения сборки в машинном коде, на котором размещена ресурсы (относительно расположения среды выполнения манифеста).|Обязательно|
|/ manifest|Имя, присваиваемое .imagemanifest созданный файл. Это также могут быть абсолютный или относительный путь для создания файла в другом месте. Имя по умолчанию совпадает с именем сборки.<br /><br /> По умолчанию: \<Текущий каталог >\\< сборки\>.imagemanifest|Optional|
|/guidName|Имя, присваиваемое символом GUID для всех образов в создаваемом манифесте.<br /><br /> По умолчанию: AssetsGuid|Optional|
|/rootPath|Корневой путь, который должен быть удален перед созданием URI управляемых ресурсов. (Этот флаг — помощь в случаях, где средство возвращает относительному пути URI, вызваны ресурсы, которые не удалось загрузить.)<br /><br /> По умолчанию: \<Текущий каталог >|Optional|
|/ RECURSIVE|Если этот флажок указывает, что для рекурсивного поиска все каталоги в аргументе /resources. Опустив этот флаг приведет только верхнего уровня поиск каталогов.|Optional|
|/isNative|Установите этот флаг, если аргумент сборки представлен путь для сборки в машинном коде. Этот флаг при опустите аргумент сборки является имя управляемой сборки. (См. Дополнительные сведения о этот флаг разделе "Примечания").|Optional|
|/newGuids|Если этот флажок указывает, что для создания нового значения для символа образы GUID вместо слияние из существующего манифеста.|Optional|
|/newIds|Если этот флажок указывает, что для создания новых значений символов идентификатор для каждого изображения вместо объединения значений из существующего манифеста.|Optional|
|/nologo|Этот параметр останавливает продукта и авторских правах, возвращенными печати.|Optional|
|/?|Выводит справочные сведения.|Optional|
|/help|Выводит справочные сведения.|Optional|

 **Примеры**

-   ManifestFromResources /resources:D:\Images                       /assembly:My.Assembly.Name                       /isNative

-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml                       /assembly:My.Assembly.Name                       /manifest:MyImageManifest.imagemanifest

-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds

## <a name="notes"></a>Примечания

-   Это средство поддерживает только файлы PNG и .xaml. Другие типы образа или файла будет игнорироваться. Предупреждение создается для всех неподдерживаемых типов обнаружения при синтаксическом анализе ресурсы. Если не поддерживается образы находятся в завершении средство синтаксического анализа ресурсы, будет сформирована ошибка

-   Следуя предполагаемый формат для образы .png, средство будет присвоено значение размера/аналитики для .png размер задан формат, даже если он отличается от фактического размера изображения.

-   Можно опустить формат ширины или высоты для изображения в формате PNG, но средство чтения изображения фактическое ширины или высоты и использовать их для изображения размером/измерения значение.

-   Запуск этого средства на одной группы изображений несколько раз для одного .imagemanifest приведет к повторяющиеся записи манифеста, так как программа пытается разделить набора изображений на автономные изображения и добавлять их в существующий манифест.

-   Слияние (пропуская /newGuids или /newIds) должна выполняться только для созданных манифестов. Манифесты, настраивали или автоматически с помощью других средств, которые не могут быть объединены неправильно.

-   Манифесты, созданные для собственных сборок может потребоваться вручную после создания, чтобы сделать символы идентификатор соответствует ресурсу идентификаторы из RC-файл машинной сборки.

## <a name="sample-output"></a>Пример результатов выполнения
 **Манифест простого образа**

 Манифеста изображения, будет выглядеть так, чтобы этот XML-файл:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15197 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" />
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <ID Name="MyImage" Value="0" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage)">
      <Source Uri="$(Resources)/Xaml/MyImage.xaml" />
      <Source Uri="$(Resources)/Png/MyImage.16.16.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>
  <ImageLists />
</ImageManifest>
```

 **Манифест изображения для полосу изображений**

 Манифест изображения для полосу изображений, будет выглядеть так, этот XML-файл:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15197 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <ID Name="MyImageStrip_0" Value="1" />
    <ID Name="MyImageStrip_1" Value="2" />
    <ID Name="MyImageStrip" Value="3" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)">
      <Source Uri="$(Resources)/MyImageStrip_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)">
      <Source Uri="$(Resources)/MyImageStrip_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>
  <ImageLists>
    <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)">
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" />
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" />
    </ImageList>
  </ImageLists>
</ImageManifest>
```

 **Манифест изображения для сборки в машинном коде графических ресурсов**

 Манифест изображения для образов в машинном коде, будет выглядеть так, этот XML-файл:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15198 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" />
    <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" />
    <ID Name="MyImage1" Value="0" />
    <ID Name="MyImage2" Value="1" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage1)">
      <Source Uri="$(Resources)">
        <Size Value="16" />
        <NativeResource ID="$(MyImage1)" Type="PNG" />
      </Source>
    </Image>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage2)">
      <Source Uri="$(Resources)">
        <Size Value="16" />
        <NativeResource ID="$(MyImage2)" Type="PNG" />
      </Source>
    </Image>
  </Images>
  <ImageLists />
</ImageManifest>
```