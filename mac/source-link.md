---
title: Отладка пакетов NuGet с помощью технологии Source Link
description: В этой статье описывается функция Source Link в Visual Studio для Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 530ad09bbf72d9696621f328c2df40b37f362c13
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2020
ms.locfileid: "75439088"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Отладка пакетов NuGet с помощью технологии Source Link

Технология Source Link дает возможность выполнять отладку исходного кода сборок .NET из NuGet, которые поставляют .PDB со ссылками на исходные файлы. Source Link выполняется при создании разработчиками пакета NuGet и внедряет метаданные системы управления версиями внутри сборки и пакета. Если в Visual Studio для Mac включена функция Source Link, среда IDE обнаружит, доступны ли исходные файлы для установленных пакетов. Затем Visual Studio для Mac предложит скачать их, что позволит подробнее просмотреть код пакета. Source Link также работает с кодом библиотеки базовых классов Mono для проектов Xamarin, что позволяет перейти к коду .NET Framework. Source Link предоставляет метаданные системы управления версиями для создания эффективной среды отладки.

> [!NOTE]
> Сейчас Visual Studio для Mac не поддерживает серверы символов. Из-за этого Source Link с метаданными, размещенными на серверах символов, не поддерживается.

## <a name="enable-source-link"></a>Включение Source Link

Чтобы включить Source Link в Visual Studio для Mac, перейдите к разделу **Visual Studio > Параметры... > Проекты > Отладчик** и убедитесь, что установлен флажок **Выполнение по шагам во внешнем коде**.

![Снимок экрана: диалоговое окно "Параметры" с установленным флажком "Выполнение по шагам во внешнем коде"](media/source-link1.png)

Параметр можно изменить в области **Download External Code** (Скачать внешний код) в соответствии с собственными предпочтениями:
* Спрашивать: Visual Studio для Mac предложит скачать внешний код.
* Всегда: Visual Studio для Mac автоматически скачает внешний код.
* Никогда: Visual Studio для Mac не будет скачивать соответствующий внешний код.

По умолчанию выбрано значение **Спрашивать**. При обнаружении внешнего кода для пакета NuGet отобразится следующий запрос:

![Снимок экрана: запрос, отображаемый при обнаружении внешнего кода для пакета NuGet](media/source-link2.png)


## <a name="see-also"></a>См. также

- [Репозиторий Source Link на GitHub](https://github.com/dotnet/sourcelink/blob/master/README.md)
- [Документация .NET](https://docs.microsoft.com/dotnet/standard/library-guidance/sourcelink) по Source Link и дополнительные сведения о добавлении поддержки Source Link в пакеты
