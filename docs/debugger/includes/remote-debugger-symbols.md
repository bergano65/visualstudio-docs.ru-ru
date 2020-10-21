---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 5033580f253a5eb42cbc64656e8c4661a2e246c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72912857"
---
Вы можете отлаживать код с использованием символов, созданных на компьютере Visual Studio. Производительность удаленного отладчика гораздо выше при использовании локальных символов.  Если необходимо использовать удаленные символы, укажите, что монитор удаленной отладки должен искать символы на удаленном компьютере.  

Начиная с версии Visual Studio 2013 с обновлением 2 можно использовать следующий параметр командной строки msvsmon для использования удаленных символов для управляемого кода: `Msvsmon /FallbackLoadRemoteManagedPdbs`  

Дополнительные сведения см. в справке по удаленной отладке (нажмите клавишу **F1** в окне удаленного отладчика или щелкните **Справка > Использование**). Также см. запись блога с описанием [изменений, связанных с удаленной загрузкой символов .NET в Visual Studio 2012 и 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/).
