---
title: ProjectItem Элемент (Visual Studio шаблоны проекта) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11052d8e585f1d06f6d787402001cfbbe2b6810f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701840"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>Элемент ProjectItem (шаблоны проекта Visual Studio)
Упогоняет файл, включенный в шаблон проекта.

> [!NOTE]
> Элемент `ProjectItem` принимает различные атрибуты в зависимости от того, является ли шаблон для проекта или элемента. Эта тема `ProjectItem` объясняет элемент для шаблонов проектов. Для объяснения `ProjectItem` элемента для шаблонов элементов см. Элемент [ProjectItem (Visual Studio Item Templates)](../extensibility/projectitem-element-visual-studio-item-templates.md).

 \<vsTemplate \<> TemplateContent \< \<> проект> projectItem>

## <a name="syntax"></a>Синтаксис

```
<ProjectItem
    TargetFileName="TargetFileName.ext"
    ReplaceParameters="true/false"
    OpenInEditor="true/false"
    OpenInWebBrowser="true/false"
    OpenInHelpBrowser="true/false"
    OpenOrder="Value">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

| Атрибут | Описание |
|---------------------| - |
| `TargetFileName` | Необязательный атрибут.<br /><br /> Упоняет имя и траекторию элемента проекта при создании проекта из шаблона. Этот атрибут полезен для создания структуры каталога, отличающейся от структуры каталога в файле *шаблона .zip,* или для использования замены параметров для создания имени элемента. |
| `ReplaceParameters` | Необязательный атрибут.<br /><br /> Значение Boolean, которое определяет, имеет ли элемент значения параметров, которые должны быть заменены при создании проекта из шаблона. Значение по умолчанию: `false`. |
| `OpenInEditor` | Необязательный атрибут.<br /><br /> Значение Boolean, которое определяет, должен ли элемент быть [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] открыт в соответствующем редакторе при создании проекта из шаблона.<br /><br /> `OpenInWebBrowser` Атрибуты `OpenInHelpBrowser` и атрибуты игнорируются на `OpenInEditor` элементе со значением `true`.<br /><br /> Значение по умолчанию — `false`. |
| `OpenInWebBrowser` | Необязательный атрибут.<br /><br /> Значение Boolean, которое определяет, следует ли открывать элемент веб-браузера при создании проекта из шаблона.<br /><br /> В веб-браузере могут быть открыты только локальные HTML-файлы и текстовые файлы. Внешние URL-адреса не могут быть открыты с помощью этого атрибута.<br /><br /> Значение по умолчанию — `false`. |
| `OpenInHelpBrowser` | Необязательный атрибут.<br /><br /> Значение Boolean, которое определяет, должен ли элемент быть открыт в телезрителе справки при создании проекта из шаблона.<br /><br /> В браузере Справка могут быть открыты только HTML-файлы и текстовые файлы, которые являются локальными для проекта. Внешние URL-адреса не могут быть открыты с помощью этого атрибута.<br /><br /> Значение по умолчанию — `false`. |
| `OpenOrder` | Необязательный атрибут.<br /><br /> Укажите числовое значение, представляющее порядок открытия элементов в соответствующих редакторах. Все значения должны быть кратными по 10. Элементы `OpenOrder` с более высокими значениями открываются первыми. |

### <a name="child-elements"></a>Дочерние элементы
 Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Project](../extensibility/project-element-visual-studio-templates.md)|Определяет файлы или каталоги для добавления в проект.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 A, `string` представляющий имя или путь к файлу в файле *шаблона .zip.*

## <a name="remarks"></a>Примечания
 `ProjectItem`является необязательным `Project`ребенком .

 Атрибут `TargetFileName` может быть использован для создания структуры каталога, отличайся от структуры каталога в файле *шаблона .zip.* Например, если файл *MyFile.vb* содержится в корне файла *шаблона .zip,* но вы хотите, чтобы файл был помещен в каталог под названием *CustomFiles* во всех проектах, созданных из шаблона, вы будете использовать следующие XML:

```xml
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>
```

 Атрибут `TargetFileName` также может быть использован для переименования файлов, содержащих международные символы в их файлах. Например, файл *шаблона .zip* не может содержать имена файлов с символами Unicode, поэтому файл должен быть переименован, прежде чем он может быть сжат в файл *.zip.* Атрибут `TargetFileName` может быть использован для установки имени файла обратно в исходное имя файла Unicode.

 Атрибут `TargetFileName` также может быть использован для переименования файлов с параметрами. Следующая процедура объясняет, как переименовать файл *MyFile.vb*, который существует в корневом каталоге файла *.zip,* в имя файла на основе имени проекта.

### <a name="to-rename-files-with-parameters"></a>Переименовывать файлы с параметрами

1. Используйте следующие XML в файле *.vstemplate:*

   ```xml
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>
   ```

2. Откройте файл проекта *(.vbproj* для [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] проекта) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]в текстовом редакторе или .

3. Найдите строку в файле проекта, который похож на следующий XML:

   ```xml
   <Compile Include="MyFile.vb">
   ```

4. Замените строку кода на следующую XML:

   ```xml
   <Compile Include="$safeprojectname$.vb">
   ```

    Когда проект создается из этого шаблона, имя файла будет основываться на имени пользователя, вписавшемся в диалоговое окно **Нового проекта,** со всеми небезопасными символами и пробелами удалены. Для получения дополнительной [информации см.](../ide/template-parameters.md)

## <a name="example"></a>Пример
 В следующем примере показаны метаданные [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] для шаблона проекта для приложения.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также
- [Ссылка на схему шаблона Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Параметры шаблона](../ide/template-parameters.md)
- [Элемент ProjectItem (шаблоны элементов Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
