# lr_op

program Geometry;

var
  { Входные данные }
  xc, r:    real;  
  x,  ym, yh, glen: real;
  dl, s: real; 

  { Выходные данные }
 
{ Для упрощение будем считать, что основания фигур всегда лежат на оси абсцисс, 
кроме случая, когда фигуры концентричы }

begin

  { Ввод исходных данных }
  writeln('Введите координату центра полукруга и радиус полукруга: xc, r = ');  {Ввод значений для полукруга}
  readln(xc, r);  
  if r < 0 then
    begin 
      writeln('Некорректно введённое значение!')
    end

  writeln('Введите координаты центра треугольника: x, ym = ');
  readln(x, ym);
  writeln('Введите длину основания треугольника: glen = '); 
  readln(glen);
  if glen < 0 then
    begin 
      writeln('Некорректно введённое значение!')
    end  
  

  {Вычисление длины высоты проведённой от центра треугольника к боковой стороне}

  dl := sqrt(sqr(glen/2)+sqr(3*(ym-yh)));
  s := (glen/2)*(yh+3*(ym-yh)+ym);
  {d = s / dl} 

  { Проверка пересечения фигур и вывод результата }
  if (x = xc) and (ym = 0) then
    begin
      writeln('Фигуры концентрические');
      writeln('Введите координату y середины основния треугольника: yh = ');
      readln(yh);
      if (r <= (s / dl)) then
        writeln('Полукруг вложен в треугольник')
    end
    
  else if ((x+(glen/2) = xc-r) or (x-(glen/2) = xc+r)) then
    writeln('Фигуры касаются')
  else if ((x+(glen/2) < xc-r) or (x-(glen/2) > xc+r)) then
    writeln('Фигуры  не пересекаются')
  else 
    writeln('Фигуры пересекаются')
  
end.















