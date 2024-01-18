## Nỗi ám ảnh của các Coder: Thuật toán sắp xếp (Sorting Algorithm).
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#### *My grandmother run faster than you code.............*
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Học lập trình trong ngành Công nghệ thông tin mà không biết Cấu trúc dữ liệu và giải thuật (CTDL & GT) tức là chưa thật sự học. Học CTDL & GT thì chắc chắn phải học các thuật toán sắp xếp cơ bản. Trong bài viết này, mình sẽ đi sâu hơn, nhìn tổng quan hơn về bài toán sắp xếp và ý nghĩa của nó trong cuộc sống.
### Bối cảnh: 
- Một trong các vấn đề ta cần quan tâm đó là tìm giá trị cực đại/cực tiểu (max/min). Ví dụ: tìm bạn nữ nặng nhất lớp, xác định học sinh ngu nhất lớp, giỏi nhất lớp, v.v
- Tất nhiên, khi ta chỉ có nhu cầu tìm max, min thì chỉ cần 1 vòng lặp là xong rồi. Tuy nhiên thực tế cuộc sống không chỉ như vậy. Ta thường sẽ tìm top 10 vận động viên bơi giỏi nhất, top 3 thành phố đông dân nhất, hoặc đơn giản là cần danh sách khen thưởng sinh viên dựa trên điểm học tập à danh sách cần được sắp xếp giảm dần theo điểm.
Bạn thử tưởng tượng xem, nhìn vào danh sách sinh viên theo mã số tăng dần, hoặc theo điểm trung bình giảm dần thì có dễ chịu hơn so với 1 danh sách lộn xộn, không có quy tắc nào ?
- Đi sâu hơn trong ngành CNTT, ta sẽ thấy việc sắp xếp dữ liệu lại vô cùng quan trọng. Trên Facebook chẳng hạn: ta cần sắp xếp, tính toán các nội dung hiện lên news feed. Tin tức nào gần đây nhất, có liên quan đến ta nhất, thường sẽ xuất hiện ở đầu bảng tin trên Facebook. Tìm kiếm trên Google cũng vậy, ta không hề mong muốn Google gợi ý cho ta biết các loại trái cây trong khi ta đang tìm kiếm rau xanh. Kết quả nào gần với từ khóa cần tìm nhất phải được xuất hiện đầu tiên. Kết quả tìm kiếm cần được Google sắp xếp sao cho những nội dung quan trọng nhất, khớp với từ khóa nhất phải hiện lên trên cùng. Chức năng tìm kiếm bạn bè của app Zalo cũng vậy. Zalo sẽ tìm kiếm những người bạn gần với ta nhất tính theo khoảng cách địa lý, như vậy cần phải sắp xếp lại danh sách bạn bè theo khoảng cách.
- Việc sắp xếp dữ liệu sẽ giúp ta tìm kiếm nhanh hơn và hỗ trợ rất nhiều cho các bài toán khác. Bài toán sắp xếp là 1 nền tảng quan trọng trong Khoa học máy tính.
- Từ những nhu cầu trên, chúng ta nghiên cứu những cách thức, phương pháp để sắp xếp dữ liệu, từ đó ra đời rất nhiều thuật toán sắp xếp.
- Một số thuật toán nổi tiếng, thông dụng hiện nay như: Bubble Sort, Interchange Sort, Selection Sort, Insertion Sort, Merge Sort, Quick Sort.
### Mục tiêu của bài viết
- Mình sẽ trình bày tổng quan các thuật toán sắp xếp dựa vào sự thực nghiệm. Mình sẽ không đào sâu về nền tảng lý thuyết vì những điều này đã nói rất nhiều trên sách vở, tài liệu.
- Bài viết trình bày về việc test các thuật toán sắp xếp và đánh giá chúng. Ngoài ra bài viết còn nói một số khía cạnh cần quan tâm khi sử dụng thuật toán sắp xếp.
### Điểm danh các thuật toán sắp xếp 
- 20 thuật toán sắp xếp sẽ được lên dĩa, chưa kể mỗi thuật toán có thể bao gồm nhiều phương pháp và cấu hình ==> tổng cộng là 24 thuật toán. Danh sách 24 thuật toán như sau:
   - BlockMerge Sort
   - BST Sort (dựa trên Binary Search Tree)
   - Bubble Sort
   - Counting Sort
   - Flash Sort
   - Heap Sort
   - Insertion Sort
   - Interchange Sort
   - Intro Sort (`std::sort`)
   - Merge Sort (cpp `std – std::stable_sort`)
   - Merge Sort (top-down)
   - Merge Sort (bottom-up)
   - Noname Sort
   - Super Noname Sort --> đây là sản phẩm của mình, cải tiến dựa trên 1 ý tưởng rất hay
   - Quick Sort
   - Quick Sort (3-way)
   - Radix Exchange Sort
   - Radix Sort 4
   - Radix Sort 8
   - Radix Sort 16
   - Selection Sort
   - Shell Sort
   - Smooth Sort
   - Tim Sort
- Mình sẽ test tất cả 24 thuật toán này và tìm ra quán quân vô địch.
- Dữ liệu chuẩn bị:
   - Source code tất cả thuật toán, mình gom lại trên 1 solution Visual Studio 2012.
   - High-resolution timer.
   - Chương trình sinh ra mảng input.
 
![image](https://github.com/MustardLawyer1995/CS-Note/assets/156400720/ee6778f4-b1d3-41e1-a305-734395ed8074)

- Với arguments ở trên, mình đã sinh ra mảng gồm 10 phần tử ngẫu nhiên, mỗi phần tử nằm trong đoạn [5, 11]. Dữ liệu xuất ra tập tin “10.txt”.

![image](https://github.com/MustardLawyer1995/CS-Note/assets/156400720/1df062f8-c465-41c8-9a88-a7f79c2a84c0)

- Tất cả thuật toán sẽ trải qua 5 test cases, mỗi test case bao gồm 3 trường hợp: mảng tăng dần, mảng giảm dần và mảng ngẫu nhiên. Mỗi thuật toán đều sắp xếp tăng dần. Ngoài ra còn có 1 test case về resource.
- Kết quả test là thời gian chạy của mỗi thuật toán (tính bằng nano giây). Chỉ đo thời gian xử lý, cụ thể hơn, thời gian được tính kể từ lúc sau khi input, xử lý và dừng khi xử lý xong --> output.
- Ghi chú: 1 giây = 1 tỉ nano-giây.
- Nào, chúng ta cùng nhau bắt đầu !
### Test 
#### Test case #1 - 10000 phần tử
- Bình thường mảng có khoảng vài chục, vài trăm phần tử là đã phê rồi. Đằng này đến 10 nghìn phần tử, có vẻ lớn ghê. Thật ra không phải như vậy, 10.000 vẫn còn quá nhỏ bé.
- Với $n = 10 000$, mỗi phần tử nằm trong đoạn $[0, 9999]$ thì đây là kết quả:

![image](https://github.com/MustardLawyer1995/CS-Note/assets/156400720/8f1df3d1-ae5d-46a3-99df-213d22a335a3)




