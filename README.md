# DLE-Favorites
Простенький модуль, который заменяет стандартный обработчик кнопки добавления в закладки. Более подробнее об отличиях в полном описании.

## Установка
1. Скопировать папку engine в корень сайта
2. Вставить JS код модуля из файла libs.js в подключенный к шаблону JS файл
3. Использовать HTML код и стили из файла sample_x.txt
4. Для DLE 13.x использовать установщик плагина из файла dle-favorites.xml
5. Внести свои параметры в конфиг файле **engine/mods/favorites/config.php**

### Ручная установка (DLE 12.x и младше)
Для более ранних версий выполнить установку вручную

- Открыть файл **engine/engine.php**

Найти строку:

`switch ( $do ) {`

Ниже нее вставить:

		case "favorites":
			$config['allow_cache'] = false;
			include ENGINE_DIR . '/modules/favorites.php';
			break;


- Открыть файл **engine/modules/favorites.php**

Найти строку:

`$order_list = array();`

Ниже нее вставить:

	require_once ENGINE_DIR . '/mods/favorites/class.favorites.php';
	$favmod = new Sandev\Favorites;
	$list = $favmod->getList();


- Открыть файл **engine/modules/main.php** (если файла нет, то в корне сайта **index.php**)

Найти строку:

`echo $tpl->result['main'];`

Выше нее вставить:

`include_once ROOT_DIR . '/engine/mods/favorites/index.php';`
