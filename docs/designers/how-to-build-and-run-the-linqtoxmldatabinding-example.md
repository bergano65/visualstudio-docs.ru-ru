---
title: "Практическое руководство. Сборка и выполнение примера LinqToXmlDataBinding | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3943deaf-80e2-4968-ac04-d3ef56cfad6c
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a90e55a60c9451229fd767dac6a8aaa0e2a2e224
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Практическое руководство. Сборка и выполнение примера LinqToXmlDataBinding
В этом разделе показано создание и построение проекта среды Visual Studio LinqToXmlDataBinding, а также запуск полученного в результате образца программы WPF LinqToXmlDataBinding.  
  
 Дополнительные сведения о создании проектов в среде Visual Studio см. на странице [Разработка приложений в Visual Studio](http://msdn.microsoft.com/en-us/97490c1b-a247-41fb-8f2c-bc4c201eff68).  
  
## <a name="creating-and-populating-the-project"></a>Создание и заполнение проекта данными  
  
#### <a name="to-create-the-starting-project"></a>Создание начального проекта  
  
1.  Запустите среду Visual Studio и создайте приложение C# WPF с именем LinqToXmlDataBinding. В проекте должна использоваться инфраструктура .NET Framework 3.5 (или более поздняя версия).  
  
2.  Добавьте в проект ссылки для следующих сборок .NET, если они еще не заданы:  
  
    -   System.Data  
  
    -   System.Data.DataSetExtensions  
  
    -   System.Xml  
  
    -   System.Xml.Linq  
  
3.  Выполните сборку решения, нажав клавиши **Ctrl+Shift+B**, и запустите его, нажав клавишу **F5**. Проект должен быть скомпилирован без ошибок и выполнен как обычное приложение WPF.  
  
#### <a name="to-add-custom-code-to-the-project"></a>Добавление в проект пользовательского кода  
  
1.  В обозревателе решений переименуйте исходный файл Window1.xaml в L2XDBForm.xaml. Зависимый исходный файл Window1.xaml.cs должен быть автоматически переименован в L2XDBForm.xaml.cs.  
  
2.  Замените исходный код в файле L2XDBForm.xaml фрагментом кода из статьи [L2DBForm.xaml Source Code](../designers/l2dbform-xaml-source-code.md) (Исходный код L2DBForm.xaml). (Для работы с этим файлом используйте представление источника данных XAML.)  
  
3.  Аналогичным образом замените исходный код в файле L2XDBForm.xaml.cs кодом из статьи [L2DBForm.xaml.cs Source Code](../designers/l2dbform-xaml-cs-source-code.md) (Исходный код L2DBForm.xaml.cs).  
  
4.  В файле App.xaml замените все вхождения строки «Window1.xaml» строкой «L2XDBForm.xaml».  
  
5.  Выполните сборку решения, нажав клавиши **Ctrl+Shift+B**.  
  
## <a name="running-the-program"></a>Выполнение программы  
 Программа LinqToXmlDataBinding дает пользователю возможность просматривать и управлять списком книг, который хранится в виде внедренного XML-элемента.  
  
#### <a name="to-run-the-program-and-view-the-book-list"></a>Выполнение программы и просмотр списка книг  
  
1.  Запустите программу LinqToXmlDataBinding, нажав клавишу **F5** (**Начать отладку**) или клавиши **Ctrl+F5** (**Запуск без отладки**). Откроется окно программы с заголовком **WPF Data Binding using LINQ to XML** (Привязка данных WPF с помощью LINQ to XML).  
  
2.  Обратите внимание на верхнюю часть пользовательского интерфейса, в котором отображается необработанный код **XML**, представляющий список книг. Он выводится с помощью элемента управления WPF <xref:System.Windows.Controls.TextBlock>, не включающего взаимодействие с мышью или клавиатурой.  
  
3.  Второй вертикальный раздел, обозначенный как **Список книг**, отображает упорядоченный список книг в виде простого текста. В нем используется элемент управления <xref:System.Windows.Controls.ListBox>, допускающий выбор с помощью мыши или клавиатуры.  
  
#### <a name="to-add-and-delete-books-from-the-list"></a>Добавление и удаление книг из списка  
  
1.  Чтобы удалить существующую книгу из списка, выделите ее в разделе **Список книг** и нажмите кнопку **Remove Selected Book** (Удалить выбранную книгу). Обратите внимание, что запись книги удаляется не только из списка, но и из необработанного исходного текста XML.  
  
2.  Чтобы добавить новую книгу в список, введите значения в элементы управления **Идентификатор** и **Значение**<xref:System.Windows.Controls.TextBox> в последнем разделе **Добавление книги**, а затем нажмите кнопку **Добавить книгу**. Обратите внимание, что новая книга добавляется в конец списка и исходного текста XML. Эта программа не выполняет проверку правильности входных значений.  
  
#### <a name="to-edit-an-existing-book-entry"></a>Редактирование существующей записи книги  
  
1.  Выделите книгу во втором разделе **Список книг**. Текущие значения для выделенной книги отобразятся в третьем разделе — **Edit Selected Book** (Редактирование выделенной книги).  
  
2.  Измените значения с клавиатуры. Как только элемент управления <xref:System.Windows.Controls.TextBox> теряет фокус, изменения автоматически распространяются на список книг и исходный текст XML.  
  
## <a name="see-also"></a>См. также  
 [Пример связывания с данными в WPF с помощью LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [Walkthrough: LinqToXmlDataBinding Example](../designers/walkthrough-linqtoxmldatabinding-example.md)  (Пошаговое руководство. Пример LinqToXmlDataBinding)  
 [Разработка приложений в Visual Studio](http://msdn.microsoft.com/en-us/97490c1b-a247-41fb-8f2c-bc4c201eff68)