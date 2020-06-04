cały projekt robicie w 3 wymiarach wszystkie operacje itd, na koniec każdej klatki tylko jest rzutowanie na 2d i wyświetlenie
- szukacie jakiejś biblioteki do c# do wyświetlania obrazu na płaszczyźnie - może to być najprostrza biblioteka graficzna, byle by móc ustawiać na canvasie odpowiednie punkty (x,y) w wybranym kolorze (jednak lepiej poszukać czegoś co od razu ma wbudowane rysowanie conajmniej prostych brył geometrycznych z wypełnieniem) - chyba biblioteka do gier 2d, bo w gratisie dostaniecie coś do zarządzania czasem
- biblioteka do macierzy - potrzebne jest mnożenie (można samemu pisać od 0, ale po co ;) )
- budujecie obiekty w świecie 3d - klasa do vektórów w 3d (x,y,z), definicja punktów dla kostki - w sumie 8 punktów (ja wrzuciłem 2 kostki w różnych miejscach, bo łatwiej debugować mając większą ilośc obiektów na scenie), dobrze te bryły ustawić by na starcie były przed nami - zakłądając jako system koordynatów "left handed" z osiami, x - w prawo, y - w górę, z - w przód, wystarczy by "z" były dodatnie
- na podstawie punktów definiujecie zbiór ścian czworokątów bądź trójkątów, z których zbudowane są kostki) - jedna ściana to np któreś 4 punkty (tak, jeden punkt moze być używany do kilku śian)
- zakładając że kamera stoi w punkci 0,0,0, robimy rzutowanie dla wszystkiego co znajduje sie na scenie używając kodu znajdującego z labktów które wysłaliście (byle z matlaba to przepisać, z tym, że "d" polecam ustawić dosyć duże, przy 10 kostki wyglądają jakby się schrzaniło opisywanie tych 8 punktów...)
- zbiór wszystkich punktów w 3d (x,y,z) przepuszczacie przez rzutowanie perspektywiczne - otrzymacie punkty w 2d (x,y)
- otrzymane punkty w 2d rysujecie na płaszczyźnie gotową funkcją z jakiejs biblioteki, rysując po całej płaszczyźnie, np: klasaDoRysowaniaZjakiejsBiblioteki.DrawTriangle(punktXYZ1, punktXYZ2, punktXYZ3) - punktXYZ to jakas klasa, która zwraca punkt w 3 wymiarach (czyli funkcja rysująca trójkąt pobiera 3 zestawy (x,y,z))

niestety ale dopiero w tym momencie widać czy czegoś się nie schrzaniło wcześniej, od tego momentu już z górki (bo cokolwiek widac...)
- dodajecie obsługe dla iteracji, czyli za każdą pętlą while rysujecie wszystko od nowa (cały powyższy kod z wyrysowaniem całości pod koniec)
- dodajecie funkcje do przemieszczania się - która musi wszystkie punkty jakie macie przemieszczać (w jakims forze), gdzie poruszenie się w przód to jest przedefiniowanie wierzchołków, np (zarys kodu):
	public MoveForward(x,y,z, odlegloscPrzemieszczenia){
		return (x, y, z - odlegloscPrzemieszczenia))
	}
	// odejmujemy, bo mając bryłę przed nami, ma ona np z=10, skoro idziemy w przód (mamy zawsze stać w 0,0,0), musimy się zbliżyć do figury, czyli zmniejszamy odległość, więc to figura ma iść do nas
- tak samo dla tyłu, lewo prawo, góra dół | czy to będzie + czy - będzie widać, że zamiast w przód będzie się wszystko rpzemieszczało w tył
- implementacja obrotów, tak samo jak przemieszcanie, z tym, że tutaj trzeba zwrócić punkty przemnożone przez macierz obrotu - macie implementacje w labkach, tyle że znowu w matlabie
- zmapowanie tego pod przyciski, czyli jakis switch(input), i pod case wrzucacie np: case Key.W : FunkcjaZMoveForwardIForemDlaWszystkichPunktow
- skalowania nie implementujemy


