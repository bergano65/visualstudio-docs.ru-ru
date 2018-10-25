---
title: Пошаговое руководство. Пример LinqToXmlDataBinding Example | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3c69c69cfed53b0080614984853b3128908c2e89
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893654"
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>Пошаговое руководство. Пример LinqToXmlDataBinding
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве описывается пример LinqToXmlDataBinding, а также разъясняются наиболее интересные элементы содержимого главных его исходных файлов L2DBForm.xaml и L2DBForm.xaml.cs.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Перед тем как вы приступите к знакомству с этим пошаговым руководством, настоятельно рекомендуем построить и запустить программу LinqToXmlDataBinding, как это описано в статье [Как построить и запустить пример LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md).  
  
## <a name="remarks"></a>Примечания  
 Программа LinqToXmlDataBinding - это приложение WPF, состоящее из файлов на языках C# и XAML. Она содержит внедренный XML-документ, который определяет список книг и дает пользователю возможность просматривать, добавлять, удалять и изменять эти записи. Она состоит из двух следующих исходных файлов.  
  
- Файл L2DBForm.xaml содержит декларацию кода XAML для пользовательского интерфейса главного окна. Он содержит также раздел ресурсов окна, который определяет поставщика данных, и внедренный XML-документ для листингов книг.  
  
- Файл L2DBForm.xaml.cs содержит методы инициализации и обработки событий, связанные с этим пользовательским интерфейсом.  
  
  Главное окно разделено по вертикали на четыре интерфейсных раздела.  
  
- Раздел **XML** отображает необработанный код внедренного листинга книг на языке XML.  
  
- Раздел **Список книг** отображает выполненные в формате стандартного текста записи книг и дает пользователю возможность выбирать и удалять отдельные записи.  
  
- Раздел **Правка выделенной книги** позволяет пользователю изменять значения, связанные с книжной записью, выделенной в данный момент.  
  
- Раздел **Добавить новую книгу** позволяет создавать новую запись в книге на базе значений, введенных пользователем.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Исходный код L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)|Включает в себя содержимое и описание кода XAML в файле L2DBForm.xaml.|  
|[Исходный код L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)|Включает в себя содержимое и описание исходного кода C# в файле L2DBForm.xaml.cs.|  
  
## <a name="see-also"></a>См. также  
 [Пример связывания с данными в WPF с помощью LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [Практическое руководство. Сборка и выполнение примера LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)



