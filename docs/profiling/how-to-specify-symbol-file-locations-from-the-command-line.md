---
title: "Практическое руководство. Определение расположения файлов символов с помощью командной строки | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 63aad78bdc7df685ca3a73ec16a9cbc87b78151f
ms.openlocfilehash: 237acc5cc58646bc9f4e1ab6d2fbe976bb7ac124
ms.contentlocale: ru-ru
ms.lasthandoff: 07/14/2017

---
# Практическое руководство. Определение расположения файлов символов с помощью командной строки
<a id="how-to-specify-symbol-file-locations-from-the-command-line" class="xliff"></a>
Для отображения сведений о символах, например имен функций и номеров строк, программе командной строки VSPerfReport необходим доступ к файлам символов (PDB) профилируемых компонентов и системным файлам Windows. Файлы символов создаются при компиляции компонента. Дополнительные сведения см. в разделе [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport автоматически выполняет поиск следующих расположений файлов символов:  
  
-   пути, указанные в параметре **/SymbolPath** или в переменной среды **_NT_SYMBOL_PATH**;  
  
-   точный локальный путь к папке, в которой был скомпилирован компонент;  
  
-   каталог, содержащий файл данных профилирования (VSP или VSPS).  
  
 Корпорация Майкрософт предоставляет PDB-файлы для многих своих продуктов через Интернет на сервере символов. Если компьютер, используемой для создания отчетов, подключен к Интернету, программа VSPerfReport подключается к серверу символов по сети для автоматического поиска сведений о символах и сохранения файлов в локальном хранилище.  
  
 Расположение файлов символов и хранилища сервера символов Майкрософт можно указать следующим образом:  
  
-   задайте переменную среды **_NT_SYMBOL_PATH**;  
  
-   добавьте параметр **/SymbolPath** в командную строку VSPerfReport.  
  
 Можно также использовать оба этих метода.  
  
> [!NOTE]
>  Если [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] установлен на локальном компьютере, расположение файлов символов Windows, вероятно, уже указано. Дополнительные сведения см. в разделе [Практическое руководство. Справочная информация о символах Windows](../profiling/how-to-reference-windows-symbol-information.md). Вам, тем не менее, потребуется настроить в VSPerfReport использование расположения и сервера, как описано далее в этом разделе.  
  
## Задание файлов символов Windows
<a id="specifying-windows-symbol-files" class="xliff"></a>  
  
#### Настройка использования сервера символов Windows
<a id="to-configure-the-use-of-the-windows-symbol-server" class="xliff"></a>  
  
1.  При необходимости создайте каталог для локального хранения файлов символов.  
  
2.  Используйте следующий синтаксис для задания переменной среды **_NT_SYMBOL_PATH** или параметра VSPerfReport /SymbolPath:  
  
     **srv\*** *LocalStore* **\*http://msdl.microsoft.com/downloads/symbols**  
  
     где *LocalStore* — путь к созданному локальному каталогу.  
  
## Задание файлов символов компонентов
<a id="specifying-component-symbol-files" class="xliff"></a>  
 Средства профилирования выполняют поиск PDB-файлов компонентов, которые требуется профилировать, в исходном расположении в компонентах или в папке, содержащей файл данных профилирования. Можно указать другие расположения для поиска, добавив один или несколько путей в переменную **_NT_SYMBOL_PATH** или в параметр **/SymbolPath**. Отделяйте пути точкой с запятой.  
  
## Пример
<a id="example" class="xliff"></a>  
 Следующая командная строка задает в качестве переменной среды **_NT_SYMBOL_PATH** сервер символов Windows и **C:\Symbols** в качестве локального каталога.  
  
 **set  _NT_SYMBOL_PATH=srv\*C:\symbols\*http://msdl.microsoft.com/downloads/symbols**  
  
 Следующая командная строка VSPerfReport добавляет каталог C:\Projects\Symbols в путь поиска с помощью параметра **/SymbolPath**.  
  
 **VSPerfReport**  *MyApp* **.exe /SymbolPath:C:\Projects\Symbols /summary:all**
