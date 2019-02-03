---
title: Как выполнить Определение расположения файлов символов с помощью командной строки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4cb6fcfac8e9f619ab99e1d96472824d6c98e51
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776182"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Как выполнить Определение расположения файлов символов с помощью командной строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для отображения сведений о символах, например имен функций и номеров строк, программе командной строки VSPerfReport необходим доступ к файлам символов (PDB) профилируемых компонентов и системным файлам Windows. Файлы символов создаются при компиляции компонента. Дополнительные сведения см. в разделе [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport автоматически выполняет поиск следующих расположений файлов символов:  
  
- пути, указанные в параметре **/SymbolPath** или в переменной среды **_NT_SYMBOL_PATH**;  
  
- точный локальный путь к папке, в которой был скомпилирован компонент;  
  
- каталог, содержащий файл данных профилирования (VSP или VSPS).  
  
  Корпорация Майкрософт предоставляет PDB-файлы для многих своих продуктов через Интернет на сервере символов. Если компьютер, используемой для создания отчетов, подключен к Интернету, программа VSPerfReport подключается к серверу символов по сети для автоматического поиска сведений о символах и сохранения файлов в локальном хранилище.  
  
  Расположение файлов символов и хранилища сервера символов Майкрософт можно указать следующим образом:  
  
- задайте переменную среды **_NT_SYMBOL_PATH**;  
  
- добавьте параметр **/SymbolPath** в командную строку VSPerfReport.  
  
  Можно также использовать оба этих метода.  
  
> [!NOTE]
>  Если [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] установлен на локальном компьютере, расположение файлов символов Windows, вероятно, уже указано. Дополнительные сведения см. в разделе [Как Справочная информация о символах Windows](../profiling/how-to-reference-windows-symbol-information.md) Вам, тем не менее, потребуется настроить в VSPerfReport использование расположения и сервера, как описано далее в этом разделе.  
  
## <a name="specifying-windows-symbol-files"></a>Задание файлов символов Windows  
  
#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Настройка использования сервера символов Windows  
  
1. При необходимости создайте каталог для локального хранения файлов символов.  
  
2. Используйте следующий синтаксис для задания переменной среды **_NT_SYMBOL_PATH** или параметра VSPerfReport /SymbolPath:  
  
    **srv\\*** *LocalStore* **\*http://msdl.microsoft.com/downloads/symbols**  
  
    где *LocalStore* — путь к созданному локальному каталогу.  
  
## <a name="specifying-component-symbol-files"></a>Задание файлов символов компонентов  
 Средства профилирования выполняют поиск PDB-файлов компонентов, которые требуется профилировать, в исходном расположении в компонентах или в папке, содержащей файл данных профилирования. Можно указать другие расположения для поиска, добавив один или несколько путей в переменную **_NT_SYMBOL_PATH** или в параметр **/SymbolPath**. Отделяйте пути точкой с запятой.  
  
## <a name="example"></a>Пример  
 Следующая командная строка задает в качестве переменной среды **_NT_SYMBOL_PATH** сервер символов Windows и **C:\Symbols** в качестве локального каталога.  
  
 **set _NT_SYMBOL_PATH=srv\*C:\symbols\*http://msdl.microsoft.com/downloads/symbols**  
  
 Следующая командная строка VSPerfReport добавляет каталог C:\Projects\Symbols в путь поиска с помощью параметра **/SymbolPath**.  
  
 **VSPerfReport**  *MyApp* **.exe /SymbolPath:C:\Projects\Symbols /summary:all**
