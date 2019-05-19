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
ms.openlocfilehash: 26d9169be242990b9ca99b4fe4fe043d56fb7f30
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65839643"
---
Вы можете отлаживать код с использованием символов, созданных на компьютере Visual Studio. Производительность удаленного отладчика гораздо выше при использовании локальных символов.  Если необходимо использовать удаленные символы, укажите, что монитор удаленной отладки должен искать символы на удаленном компьютере.  

Начиная с версии Visual Studio 2013 с обновлением 2 можно использовать следующий параметр командной строки msvsmon для использования удаленных символов для управляемого кода: `Msvsmon /FallbackLoadRemoteManagedPdbs`  

Дополнительные сведения см. в справке по удаленной отладке (нажмите клавишу **F1** в окне удаленного отладчика или щелкните **Справка > Использование**). Также см. запись блога с описанием [изменений, связанных с удаленной загрузкой символов .NET в Visual Studio 2012 и 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx).
