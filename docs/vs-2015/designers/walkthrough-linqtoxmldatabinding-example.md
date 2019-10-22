---
title: Пошаговое руководство. Пример LinqToXmlDataBinding Example | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e97d612e19f64110f3090029dcff82acbad8e87
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663973"
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>Пошаговое руководство. Пример LinqToXmlDataBinding
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве описывается пример LinqToXmlDataBinding, а также разъясняются наиболее интересные элементы содержимого главных его исходных файлов L2DBForm.xaml и L2DBForm.xaml.cs.

## <a name="prerequisites"></a>Необходимые компоненты
 Перед тем как вы приступите к знакомству с этим пошаговым руководством, настоятельно рекомендуем построить и запустить программу LinqToXmlDataBinding, как это описано в статье [Как построить и запустить пример LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md).

## <a name="remarks"></a>Заметки
 Программа LinqToXmlDataBinding - это приложение WPF, состоящее из файлов на языках C# и XAML. Она содержит внедренный XML-документ, который определяет список книг и дает пользователю возможность просматривать, добавлять, удалять и изменять эти записи. Она состоит из двух следующих исходных файлов.

- Файл L2DBForm.xaml содержит декларацию кода XAML для пользовательского интерфейса главного окна. Он содержит также раздел ресурсов окна, который определяет поставщика данных, и внедренный XML-документ для листингов книг.

- Файл L2DBForm.xaml.cs содержит методы инициализации и обработки событий, связанные с этим пользовательским интерфейсом.

  Главное окно разделено по вертикали на четыре интерфейсных раздела.

- Раздел **XML** отображает необработанный код внедренного листинга книг на языке XML.

- Раздел **Список книг** отображает выполненные в формате стандартного текста записи книг и дает пользователю возможность выбирать и удалять отдельные записи.

- Раздел **Правка выделенной книги** позволяет пользователю изменять значения, связанные с книжной записью, выделенной в данный момент.

- Раздел **Добавить новую книгу** позволяет создавать новую запись в книге на базе значений, введенных пользователем.

## <a name="in-this-section"></a>Содержание

|Раздел|Описание|
|-----------|-----------------|
|[Исходный код L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)|Включает в себя содержимое и описание кода XAML в файле L2DBForm.xaml.|
|[L2DBForm.xaml.cs Source Code](../designers/l2dbform-xaml-cs-source-code.md)|Включает в себя содержимое и описание исходного кода C# в файле L2DBForm.xaml.cs.|

## <a name="see-also"></a>См. также раздел
 [Привязка данных WPF с помощью LINQ to XML пример](../designers/wpf-data-binding-using-linq-to-xml-example.md) [. Создание и запуск примера LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)
