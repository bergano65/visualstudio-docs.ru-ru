---
title: "Из ресурсов манифеста | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 297d9535a8e9655ed87230d4f947faeb29e08487
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="manifest-from-resources"></a>Ресурсы манифеста
Манифест из ресурсов средство является консольным приложением, которое принимает список ресурсов изображений (.png или .xaml-файлы) и создает файл .imagemanifest, который позволяет этих образов для использования с служба образов в Visual Studio. Кроме того это средство можно использовать для добавления существующего .imagemanifest изображений. Это средство можно использовать для добавления поддержку высоким Разрешением и темы для изображений в расширение Visual Studio. .Imagemanifest созданный файл следует состава и развернут как часть расширений Visual Studio (VSIX).  
  
## <a name="how-to-use-the-tool"></a>Как использовать средство  
 **Синтаксис**  
  
 ManifestFromResources /resources:\<Dir1 >;\< Img1 >/Assembly:\<AssemblyName > \<необязательно Args >  
  
 **Аргументы**  
  
||||  
|-|-|-|  
|**Имя коммутатора**|**Примечания**|**Обязательный или необязательный**|  
|/Resources|Разделенный точками с запятой список изображений или каталоги. Этот список всегда должен содержать полный список изображений, которые будут находиться в манифесте. Если дано неполный список записей, которые не включены, будут потеряны.<br /><br /> Если файл данному ресурсу полосу изображений, средство будет разбейте его на отдельные изображения перед добавлением каждого subimage в манифест.<br /><br /> Если изображение PNG-файл, мы рекомендуем форматировать имя следующим образом, чтобы средство можно заполнить вправо атрибуты для образа: \<имя >.\< Ширина >. \<Высота > .png.|Обязательно|  
|/ Assembly|Имя управляемой сборки (без расширения) или путь выполнения сборки в машинном коде, который содержит ресурсы (относительно расположения среды выполнения манифеста).|Обязательно|  
|параметр/MANIFEST|Имя должно быть присвоено .imagemanifest созданного файла. Это можно также указать абсолютный или относительный путь, для создания файла в другом месте. Имя по умолчанию соответствует имени сборки.<br /><br /> По умолчанию: \<текущий каталог >\\< сборки\>.imagemanifest|Optional|  
|/guidName|Имя, присваиваемое символом GUID для всех образов в создаваемом манифесте.<br /><br /> По умолчанию: AssetsGuid|Optional|  
|/rootPath|Корневой путь, который должен быть отброшены перед созданием URI управляемых ресурсов. (Этот флаг доступен для случаев, когда средство возвращает относительному пути URI неправильно, вызывая ресурсов, которые не удалось загрузить).<br /><br /> По умолчанию: \<текущий каталог >|Optional|  
|/ RECURSIVE|Установка этого флажка указывает, что для рекурсивного поиска все каталоги в аргументе /resources. Пропуск этот флаг приведет только верхнего уровня поиска каталогов.|Optional|  
|/isNative|Установите этот флаг, если аргумент сборки представляет путь для сборки в машинном коде. Не указывайте этот флаг, при сборке аргумент является именем для управляемой сборки. (См. раздел Примечания для дополнительных сведений о этот флаг).|Optional|  
|/newGuids|Установка этого флажка указывает, что для создания нового значения для символа образы GUID вместо слияние из существующего манифеста.|Optional|  
|/newIds|Установка этого флажка указывает, что для создания новых значений символов идентификатор для каждого изображения вместо объединения значений из существующего манифеста.|Optional|  
|/nologo|Этот флаг установлен останавливает продукта и авторских правах информацию от печати.|Optional|  
|/?|Выводит справку.|Optional|  
|/help|Выводит справку.|Optional|  
  
 **Примеры**  
  
-   ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds  
  
## <a name="notes"></a>Примечания  
  
-   Средство поддерживает только файлы .png и .xaml. Другие типы изображений или файла будет игнорироваться. Предупреждение для всех типов не поддерживается, при синтаксическом анализе ресурсы. Если не поддерживается изображения найдены после завершения средство синтаксического анализа ресурсы, будет сформирована ошибка  
  
-   Следуя предполагаемый формат для изображений в формате PNG, средство будет присвоено значение размера или измерений .png размер задан формат, даже если он отличается от фактического размера изображения.  
  
-   Можно опустить формат ширины или высоты для изображений в формате PNG, но средство чтения фактическое изображение ширины или высоты и использовать их для изображения значение размера или измерений.  
  
-   При запуске этого средства на же изображений несколько раз для одного .imagemanifest приведет повторяющиеся записи манифеста, так как средство пытается разделить набора изображений на автономные изображения и добавить их в существующий манифест.  
  
-   Слияние (опустив /newGuids или /newIds) должно использоваться только для созданных средствами манифестов. Манифесты, созданный с помощью других средств или настроить не могут быть объединены неправильно.  
  
-   Манифесты, созданные для машинные сборки может потребоваться изменить вручную после формирования, чтобы сделать символы идентификатор, который соответствует ресурсу идентификаторы из RC-файла машинной сборки.  
  
## <a name="sample-output"></a>Пример результатов выполнения  
 **Манифест простой изображения**  
  
 Манифест изображения будет выглядеть этот XML-файл:  
  
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
  
 **Манифест изображения для изображений**  
  
 Манифест изображения для изображений будет выглядеть этот XML-файл:  
  
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
  
 **Манифест изображения для сборки в машинном коде графические ресурсы**  
  
 Манифест изображения для образов в машинном коде, будет выглядеть этот XML-файл:  
  
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