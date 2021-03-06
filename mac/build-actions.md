---
title: Действия при сборке
description: В этой статье описываются различные действия сборки, которые могут использоваться для проектов C#
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d089f38bd91eda2565f215e8d15a74cc119b8767
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73714399"
---
# <a name="build-actions"></a>Действия при сборке

Все файлы в проекте Visual Studio для Mac имеют действие при сборке. Оно определяет, что происходит с файлом во время сборки. 

>[!NOTE]
>Этот раздел относится к Visual Studio для Mac. Для Visual Studio в Windows см. раздел [Действия сборки](/visualstudio/ide/build-actions).

## <a name="set-a-build-action"></a>Задание действия при сборке

Чтобы настроить действие сборки для файла в Visual Studio для Mac, можно щелкнуть правой кнопкой мыши любой файл и выбрать **Действие при сборке**, как показано ниже.

![Выбор действия сборки Compile в обозревателе решений](media/projects-and-solutions-image1.png)

Действия сборки для этого файла будут показаны во всплывающем меню. 

## <a name="build-action-values"></a>Значения действий при сборке

Вот некоторые стандартные действия сборки для проектов в Visual Studio для Mac.

|Действие при сборке | Типы проектов | ОПИСАНИЕ |
|--|--|--|
| **Compile** | Любое действие | Файл передается компилятору C# в виде файла исходного кода.|
| **Содержимое** | .NET, Xamarin | Для проектов ASP.NET эти файлы включаются в состав сайта при его развертывании. Для проектов Xamarin.iOS и Xamarin.Mac они будут включены в пакет приложений.|
| **Embedded Resource** | .NET | Файл передается компилятору C# в виде ресурса, внедряемого в сборку. После этого можно использовать [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream) из пространства имен `System.Reflection` для чтения файла из сборки.|
| **None** | Любое действие | Файл не является частью сборки. Он включен в проект для упрощения доступа из интегрированной среды разработки. Это значение можно использовать для файлов документации, например файлов сведений.|

> [!NOTE]
> Для проектов конкретных типов могут определяться дополнительные действия сборки, поэтому список действий сборки зависит от типа проекта и в нем могут присутствовать значения, отсутствующие в этом списке.  

Проекты Xamarin.iOS имеют действие при сборке **BundleResource**, которое добавляет файл как часть пакета приложений. Сведения о действиях при сборке для Xamarin.Android см. в руководстве по [процессу сборки](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions).

Можно также выбрать несколько файлов в обозревателе решений, чтобы задать действие сборки сразу для большого числа файлов.

## <a name="see-also"></a>См. также

- [Действия сборки (Visual Studio в Windows)](/visualstudio/ide/build-actions)