---
title: Действия при сборке для файлов
ms.date: 11/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5eb4c000973afd1eef92d283e5688862413add16
ms.sourcegitcommit: f61ad0e8babec8810295f039e67629f4bdebeef0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/19/2018
ms.locfileid: "52002131"
---
# <a name="build-actions"></a>Действия при сборке

Все файлы в проекте Visual Studio имеют действие при сборке. Действие при сборке определяет, что происходит с файлом при компиляции проекта.

> [!NOTE]
> Этот раздел относится к Visual Studio в Windows. Информацию о Visual Studio для Mac см. в статье [Действия при сборке в Visual Studio для Mac](/visualstudio/mac/build-actions).

## <a name="set-a-build-action"></a>Задание действия при сборке

Чтобы задать действие при сборке для файла, откройте свойства в окне **Свойства**, выбрав файл в **обозревателе решений** и нажав клавиши **ALT**+**ВВОД**. Либо щелкните правой кнопкой мыши файл в **обозревателе решений** и выберите пункт **Свойства**. В разделе **Дополнительно** окна **Свойства** используйте стрелку раскрывающегося списка рядом с полем **Действие при сборке**, чтобы задать действие при сборке для файла.

![Действия при сборке для файла в Visual Studio](media/build-actions.png)

## <a name="build-action-values"></a>Значения действий при сборке

Некоторые действия при сборке для файлов проекта C# и Visual Basic:

* **None** — файл не является частью сборки. Это значение можно использовать для файлов документации, например файлов сведений.
* **Compile** — файл передается компилятору в виде файла исходного кода.
* **Content** — файл, помеченный как **Content**, можно извлечь в виде потока, вызвав <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType>. Для проектов ASP.NET эти файлы включаются в состав сайта при его развертывании.
* **Embedded Resource** — файл передается компилятору C# в виде ресурса, внедряемого в сборку. Вы можете вызвать <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> для чтения файла из сборки.
* **AdditionalFiles** — текстовый файл, не связанный с исходным кодом и передаваемый компилятору C# или Visual Basic в качестве входных данных. Это действие при сборке используется в основном для передачи входных данных в [анализаторы](../code-quality/roslyn-analyzers-overview.md), на которые ссылается проект, для проверки качества кода. Дополнительные сведения см. в разделе [Использование дополнительных файлов](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md).

## <a name="see-also"></a>См. также

- [Параметры компилятора C#](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Параметры компилятора Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Действия при сборке (Visual Studio для Mac)](/visualstudio/mac/build-actions)