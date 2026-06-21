TRƯỜNG ĐẠI HỌC KỸ THUẬT CÔNG NGHIỆP
KHOA ĐIỆN TỬ

TIỂU LUẬN
MÔN :HỆ QUẢN TRỊ CSDL PHÂN TÁN
ĐỀ TÀI:
Higher-order bugs và giới hạn của kiểm thử

GVHD	:	Ths. NGUYỄN THỊ HƯƠNG
HỌ VÀ TÊN SINH VIÊN	:
	MA QUỐC HIẾU
TẠ PHẠM ĐÌNH HÒA
MSSV
Lớp : K58.KTP                                                  	:
:	K225480106089
K225480106088





THÁI NGUYÊN - 2026
TRƯỜNG ĐHKTCN	CỘNG HOÀ XÃ HỘI CHỦ NGHĨA VIỆT NAM
KHOA ĐIỆN TỬ	Độc lập - Tự do - Hạnh phúc

PHIẾU GIAO NHIỆM VỤ 
Sinh viên : Ma Quốc Hiếu                  MSSV: K225480106089
Sinh viên : Tạ Phạm Đình Hòa           MSSV: K225480106088
Lớp: K58KTP                                              Khoá: 2022-2027
Bộ môn: Công Nghệ Thông Tin
Giáo viên hướng dẫn: Ths. Nguyễn Thị Hương 
1. Tên đề tài: Higher-order bugs và giới hạn của kiểm thử
2. Nội dung thực hiện :
Nhiệm vụ thực hiện của đề tài tập trung vào việc nghiên cứu lý thuyết tổng quan về kiểm thử phần mềm và đi sâu phân tích bản chất, đặc điểm cũng như các nguyên nhân cốt lõi hình thành lỗi bậc cao (Higher-order Bugs). Trên cơ sở đó, đề tài xây dựng các phương pháp phát hiện, quy trình xử lý loại lỗi phức tạp này thông qua kiểm thử tích hợp, kiểm thử hệ thống và kiểm thử hiệu năng. Đồng thời, nghiên cứu làm rõ các giới hạn bất biến về mặt lý thuyết và thực tiễn của hoạt động kiểm thử như rào cản về thời gian, chi phí, môi trường hay hiện tượng nghịch lý thuốc trừ sâu. Từ các kết quả phân tích, đề tài đề xuất bộ giải pháp toàn diện từ cải thiện thiết kế hệ thống, áp dụng tự động hóa, quy trình CI/CD đến giám sát sau triển khai nhằm nâng cao hiệu quả kiểm thử và giảm thiểu tối đa rủi ro cho phần mềm
3. Ngày giao nhiệm vụ: 02/05/2026
4. Ngày hoàn thành nhiệm vụ: 18/06/2026
          SINH VIÊN	                                GIÁO VIÊN HƯỚNG DẪN
(Ký và ghi rõ họ tên)	                             (Ký và ghi rõ họ tên)



                                                                                        
NHẬN XÉT CỦA GIÁO VIÊN HƯỚNG DẪN
…………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………..

Thái Nguyên, ngày….tháng…..năm 20....
            						  GIÁO VIÊN HƯỚNG DẪN
               							(Ký và ghi rõ họ tên)























MỤC LỤC







































LỜI CAM ĐOAN          

























LỜI NÓI ĐẦU
Trong những năm gần đây, ngành công nghiệp phần mềm đã có những bước phát triển mạnh mẽ và trở thành một phần không thể thiếu trong nhiều lĩnh vực của đời sống. Chất lượng phần mềm là yếu tố quan trọng quyết định sự thành công của sản phẩm cũng như mức độ hài lòng của người sử dụng. Chính vì vậy, hoạt động kiểm thử phần mềm ngày càng được chú trọng trong quá trình phát triển hệ thống.
Tuy nhiên, việc đảm bảo chất lượng phần mềm không chỉ dừng lại ở việc phát hiện các lỗi đơn giản mà còn phải đối mặt với những lỗi phức tạp phát sinh do sự tương tác giữa nhiều thành phần trong hệ thống. Những lỗi này được gọi là Higher-order Bugs và thường rất khó phát hiện bằng các phương pháp kiểm thử thông thường. Bên cạnh đó, hoạt động kiểm thử cũng tồn tại nhiều giới hạn về thời gian, chi phí, nguồn lực và phạm vi kiểm thử.
Xuất phát từ thực tế đó, đề tài "Higher-order Bugs và Giới hạn của kiểm thử" được thực hiện nhằm tìm hiểu bản chất của Higher-order Bugs, các nguyên nhân hình thành, phương pháp phát hiện và xử lý, đồng thời phân tích những giới hạn vốn có của hoạt động kiểm thử phần mềm. Qua đó giúp nâng cao nhận thức về vai trò của kiểm thử trong việc đảm bảo chất lượng sản phẩm phần mềm.










CHƯƠNG 1: TỔNG QUAN VỀ KIỂM THỬ PHẦN MỀM
1.1 Giới thiệu về kiểm thử phần mềm
Trong thời đại công nghệ thông tin phát triển mạnh mẽ, phần mềm đã trở thành một thành phần quan trọng trong hầu hết các lĩnh vực của đời sống như giáo dục, y tế, ngân hàng, thương mại điện tử, giao thông vận tải và quản lý hành chính. Chất lượng của phần mềm ảnh hưởng trực tiếp đến hiệu quả hoạt động của tổ chức cũng như trải nghiệm của người sử dụng. Do đó, việc đảm bảo chất lượng phần mềm luôn là một yêu cầu quan trọng trong quá trình phát triển hệ thống.
Kiểm thử phần mềm (Software Testing) là một trong những hoạt động quan trọng nhất nhằm đánh giá chất lượng sản phẩm phần mềm trước khi đưa vào sử dụng. Quá trình kiểm thử giúp phát hiện các lỗi còn tồn tại, xác minh rằng phần mềm hoạt động đúng theo yêu cầu và giảm thiểu các rủi ro có thể phát sinh khi triển khai thực tế.
Trong thực tế, không có phần mềm nào hoàn toàn không có lỗi. Vì vậy, mục tiêu của kiểm thử không phải là chứng minh phần mềm hoàn hảo mà là phát hiện càng nhiều lỗi càng tốt trước khi sản phẩm được bàn giao cho người sử dụng.
1.2 Khái niệm kiểm thử phần mềm
Theo các tài liệu chuyên ngành, kiểm thử phần mềm là quá trình thực hiện chương trình hoặc hệ thống nhằm tìm ra các lỗi và đánh giá xem hệ thống có đáp ứng các yêu cầu đã được xác định hay không.
Kiểm thử được thực hiện xuyên suốt trong vòng đời phát triển phần mềm. Hoạt động này không chỉ giúp phát hiện lỗi mà còn hỗ trợ đánh giá mức độ ổn định, hiệu năng, bảo mật và khả năng đáp ứng nhu cầu của người dùng.
Ngày nay, kiểm thử phần mềm đã trở thành một lĩnh vực chuyên biệt với nhiều phương pháp, kỹ thuật và công cụ hỗ trợ khác nhau nhằm nâng cao chất lượng sản phẩm.
1.3 Vai trò của kiểm thử phần mềm
Kiểm thử phần mềm có vai trò vô cùng quan trọng trong quá trình phát triển sản phẩm.
Thứ nhất, kiểm thử giúp phát hiện lỗi trước khi hệ thống được triển khai thực tế. Việc phát hiện lỗi sớm sẽ giúp giảm chi phí sửa chữa và hạn chế những thiệt hại có thể xảy ra sau khi sản phẩm được đưa vào sử dụng.
Thứ hai, kiểm thử giúp nâng cao chất lượng phần mềm. Thông qua các hoạt động đánh giá và xác minh, nhóm phát triển có thể cải thiện độ ổn định và độ tin cậy của hệ thống.
Thứ ba, kiểm thử giúp giảm thiểu rủi ro trong quá trình vận hành. Các lỗi nghiêm trọng liên quan đến dữ liệu, bảo mật hoặc hiệu năng có thể được phát hiện và xử lý trước khi gây ảnh hưởng đến người dùng.
Thứ tư, kiểm thử góp phần nâng cao sự hài lòng của khách hàng. Một phần mềm hoạt động ổn định, dễ sử dụng và đáp ứng đúng nhu cầu sẽ tạo được sự tin tưởng từ phía người dùng.
1.4 Mục tiêu của kiểm thử phần mềm
Các mục tiêu chính của kiểm thử phần mềm bao gồm:
Phát hiện lỗi trong hệ thống
Đánh giá chất lượng phần mềm.
Kiểm tra mức độ đáp ứng yêu cầu của khách hàng.
Xác minh tính chính xác của các chức năng.
Giảm thiểu rủi ro trong quá trình triển khai.
Hỗ trợ cải tiến và nâng cấp hệ thống.
Ngoài ra, kiểm thử còn giúp các nhà phát triển hiểu rõ hơn về hành vi của hệ thống và xác định các khu vực tiềm ẩn nhiều lỗi.
1.5 Các nguyên tắc kiểm thử phần mềm
Nguyên tắc 1: Kiểm thử chỉ chứng minh sự tồn tại của lỗi
Kiểm thử có thể phát hiện lỗi nhưng không thể chứng minh hệ thống hoàn toàn không có lỗi. Dù đã thực hiện rất nhiều trường hợp kiểm thử, vẫn có khả năng tồn tại các lỗi chưa được phát hiện.
Nguyên tắc 2: Không thể kiểm thử toàn bộ
Đối với các hệ thống lớn, số lượng dữ liệu đầu vào và các trường hợp sử dụng là vô cùng lớn. Do đó, việc kiểm thử toàn bộ là không khả thi về mặt thời gian và chi phí.
Nguyên tắc 3: Kiểm thử nên được thực hiện sớm
Việc phát hiện lỗi ở giai đoạn đầu sẽ giúp giảm đáng kể chi phí sửa chữa so với việc phát hiện lỗi ở giai đoạn triển khai hoặc bảo trì.
Nguyên tắc 4: Lỗi thường tập trung
Theo nguyên lý Pareto, phần lớn lỗi thường tập trung ở một số ít module hoặc chức năng nhất định trong hệ thống.
Nguyên tắc 5: Kiểm thử phải được cập nhật
Khi phần mềm thay đổi hoặc được nâng cấp, các trường hợp kiểm thử cũng cần được cập nhật để phù hợp với phiên bản mới.
Nguyên tắc 6: Kiểm thử phụ thuộc vào ngữ cảnh
Mỗi loại phần mềm sẽ có chiến lược kiểm thử khác nhau. Ví dụ, hệ thống ngân hàng yêu cầu kiểm thử nghiêm ngặt hơn so với một website giới thiệu thông tin.
Nguyên tắc 7: Không có kiểm thử hoàn hảo
Mọi phương pháp kiểm thử đều có giới hạn riêng. Do đó cần kết hợp nhiều kỹ thuật khác nhau để nâng cao hiệu quả phát hiện lỗi.
1.6 Các mức kiểm thử
1.6.1 Kiểm thử đơn vị (Unit Testing)
Kiểm thử đơn vị tập trung vào việc kiểm tra các thành phần nhỏ nhất của chương trình như hàm, phương thức hoặc module.
Mục tiêu của Unit Testing là đảm bảo từng thành phần hoạt động chính xác trước khi được tích hợp với các thành phần khác.
1.6.2 Kiểm thử tích hợp (Integration Testing)
Kiểm thử tích hợp được thực hiện sau khi các module được kết nối với nhau.
Mục tiêu là phát hiện các lỗi phát sinh do sự tương tác giữa các thành phần trong hệ thống.
1.6.3 Kiểm thử hệ thống (System Testing)
Kiểm thử hệ thống đánh giá toàn bộ hệ thống trong môi trường hoàn chỉnh.Tại giai đoạn này, phần mềm được kiểm tra dựa trên các yêu cầu chức năng và phi chức năng đã được xác định.
1.6.4 Kiểm thử chấp nhận (Acceptance Testing)
Đây là giai đoạn kiểm thử cuối cùng trước khi triển khai thực tế.Khách hàng hoặc người dùng cuối sẽ tham gia đánh giá để xác nhận hệ thống đáp ứng các yêu cầu kinh doanh.
1.7 Các loại kiểm thử phổ biến
Kiểm thử chức năng (Functional Testing)
Đánh giá các chức năng của hệ thống dựa trên yêu cầu đã xác định.
Kiểm thử phi chức năng (Non-Functional Testing)
Đánh giá các yếu tố như hiệu năng, bảo mật, khả năng mở rộng và tính dễ sử dụng.
Kiểm thử hồi quy (Regression Testing)
Đảm bảo các thay đổi mới không làm ảnh hưởng đến các chức năng đã hoạt động ổn định trước đó.
Kiểm thử hiệu năng (Performance Testing)
Đánh giá tốc độ xử lý và khả năng đáp ứng của hệ thống.
Kiểm thử bảo mật (Security Testing)
Phát hiện các lỗ hổng bảo mật và đánh giá khả năng chống lại các cuộc tấn công.
Kiểm thử khả năng sử dụng (Usability Testing)
Đánh giá mức độ thân thiện và dễ sử dụng của giao diện đối với người dùng.
1.8 Tầm quan trọng của kiểm thử trong phát triển phần mềm hiện đại
Trong bối cảnh các hệ thống phần mềm ngày càng phức tạp và quy mô lớn, kiểm thử đóng vai trò then chốt trong việc đảm bảo chất lượng sản phẩm. Các mô hình phát triển hiện đại như Agile, DevOps và Continuous Integration đều coi kiểm thử là một phần không thể thiếu trong quy trình phát triển.
Việc áp dụng kiểm thử hiệu quả giúp doanh nghiệp tiết kiệm chi phí, giảm thiểu rủi ro và nâng cao khả năng cạnh tranh trên thị trường. Đồng thời, kiểm thử cũng là cơ sở để xây dựng những sản phẩm phần mềm ổn định, đáng tin cậy và đáp ứng tốt nhu cầu của người sử dụng.
1.9 Kết luận chương
Chương 1 đã trình bày các kiến thức tổng quan về kiểm thử phần mềm, bao gồm khái niệm, vai trò, mục tiêu, các nguyên tắc và các mức kiểm thử phổ biến. Những nội dung này là cơ sở lý thuyết quan trọng để nghiên cứu sâu hơn về Higher-order Bugs và các giới hạn của hoạt động kiểm thử trong các chương tiếp theo.



















CHƯƠNG 2: HIGHER-ORDER BUGS TRONG KIỂM THỬ PHẦN MỀM
2.1 Khái niệm Higher-order Bugs
Trong quá trình phát triển phần mềm, các lỗi xuất hiện với nhiều mức độ và hình thức khác nhau. Một số lỗi có thể được phát hiện dễ dàng thông qua kiểm thử đơn vị hoặc kiểm thử chức năng. Tuy nhiên, có những lỗi chỉ xuất hiện khi nhiều thành phần của hệ thống tương tác với nhau. Những lỗi này được gọi là Higher-order Bugs.
Higher-order Bugs là các lỗi phát sinh do sự kết hợp hoặc tương tác giữa nhiều module, nhiều chức năng hoặc nhiều thành phần khác nhau trong hệ thống phần mềm. Các thành phần này có thể hoạt động chính xác khi được kiểm tra riêng lẻ nhưng lại gây ra lỗi khi hoạt động đồng thời hoặc khi trao đổi dữ liệu với nhau.
Đây là nhóm lỗi có mức độ phức tạp cao và thường khó phát hiện hơn so với các lỗi thông thường.
2.2 Đặc điểm của Higher-order Bugs
Higher-order Bugs có một số đặc điểm nổi bật như sau:
Tính phức tạp cao
Các lỗi này không xuất hiện tại một vị trí cụ thể mà thường liên quan đến nhiều thành phần khác nhau của hệ thống.
Khó tái hiện
Trong nhiều trường hợp, lỗi chỉ xuất hiện khi một số điều kiện đặc biệt xảy ra đồng thời. Điều này khiến quá trình tái hiện lỗi trở nên khó khăn.
Khó xác định nguyên nhân
Khi lỗi xảy ra, việc xác định chính xác thành phần nào gây ra lỗi thường mất nhiều thời gian và công sức.
Phát sinh trong môi trường thực tế
Nhiều Higher-order Bugs không xuất hiện trong môi trường kiểm thử mà chỉ xuất hiện khi hệ thống hoạt động thực tế với số lượng lớn người dùng.
2.3 Phân biệt Higher-order Bugs và lỗi thông thường
Lỗi thông thường thường xuất hiện trong một chức năng hoặc module cụ thể. Nguyên nhân và vị trí lỗi tương đối dễ xác định.
Trong khi đó, Higher-order Bugs xuất hiện do sự tương tác giữa nhiều thành phần khác nhau. Các module riêng lẻ có thể hoạt động hoàn toàn chính xác nhưng khi tích hợp lại phát sinh lỗi.
Ví dụ:
Một chức năng đăng nhập hoạt động bình thường.
Một chức năng phân quyền hoạt động bình thường.
Tuy nhiên sau khi người dùng đăng nhập, hệ thống lại cấp sai quyền truy cập.
Đây là một Higher-order Bug vì lỗi chỉ xuất hiện khi hai chức năng kết hợp với nhau.
2.4 Các loại Higher-order Bugs phổ biến
Lỗi tương tác dữ liệu
Xảy ra khi dữ liệu được truyền giữa các module không chính xác hoặc không đồng nhất.
Ví dụ:
Module A gửi dữ liệu theo định dạng này nhưng Module B lại xử lý theo định dạng khác.
Lỗi xử lý đồng thời
Xuất hiện khi nhiều tiến trình hoặc nhiều người dùng cùng truy cập tài nguyên tại một thời điểm.
Ví dụ:
Hai người dùng cùng sửa một bản ghi dữ liệu dẫn đến mất dữ liệu.
Lỗi tích hợp
Xuất hiện khi các thành phần riêng lẻ được ghép nối với nhau.
Ví dụ:
Sau khi tích hợp cổng thanh toán vào website thương mại điện tử, dữ liệu đơn hàng không được cập nhật chính xác.
Lỗi bảo mật
Các chức năng riêng lẻ đều an toàn nhưng khi kết hợp lại tạo ra lỗ hổng bảo mật.
Ví dụ:
Một API công khai vô tình cho phép truy cập dữ liệu nội bộ.
Lỗi hiệu năng
Các module riêng lẻ hoạt động nhanh nhưng khi kết hợp lại gây tắc nghẽn hệ thống.
2.5 Ví dụ thực tế về Higher-order Bugs
Ví dụ 1: Hệ thống ngân hàng trực tuyến
Chức năng chuyển tiền hoạt động bình thường.
Chức năng cập nhật số dư cũng hoạt động bình thường.
Tuy nhiên khi có nhiều giao dịch cùng lúc, số dư tài khoản bị tính sai.
Ví dụ 2: Hệ thống thương mại điện tử
Chức năng đặt hàng hoạt động bình thường.
Chức năng thanh toán hoạt động bình thường.
Chức năng quản lý kho hoạt động bình thường.
Khi khách hàng thanh toán thành công, hệ thống không trừ số lượng tồn kho.
Ví dụ 3: Hệ thống đặt vé máy bay
Chức năng đặt vé hoạt động đúng.
Chức năng hủy vé hoạt động đúng.
Tuy nhiên khi khách hàng hủy vé và đặt lại trong thời gian ngắn, hệ thống ghi nhận sai số lượng ghế trống.
2.6 Tác động của Higher-order Bugs
Higher-order Bugs có thể gây ra nhiều hậu quả nghiêm trọng:
Ảnh hưởng đến dữ liệu
Dữ liệu có thể bị mất, sai lệch hoặc không đồng nhất.
Giảm độ tin cậy của hệ thống
Người dùng mất niềm tin khi hệ thống hoạt động không ổn định.
Tăng chi phí bảo trì
Do khó xác định nguyên nhân nên chi phí sửa lỗi thường cao.
Gây thiệt hại tài chính
Đặc biệt đối với các hệ thống ngân hàng, thương mại điện tử hoặc thanh toán trực tuyến.
Ảnh hưởng đến uy tín doanh nghiệp
Những lỗi nghiêm trọng có thể làm giảm hình ảnh và uy tín của tổ chức.
2.7 Tại sao Higher-order Bugs khó phát hiện
Có nhiều nguyên nhân khiến loại lỗi này khó phát hiện:
Xuất hiện trong những điều kiện đặc biệt.
Liên quan đến nhiều module khác nhau.
Không phải lúc nào cũng tái hiện được
Có thể phụ thuộc vào môi trường triển khai.
Phát sinh khi số lượng người dùng lớn.
Chỉ xuất hiện sau một thời gian hệ thống vận hành.
Trong nhiều dự án thực tế, các Higher-order Bugs chỉ được phát hiện sau khi sản phẩm đã đưa vào sử dụng.
2.8 Vai trò của kiểm thử trong việc phát hiện Higher-order Bugs
Kiểm thử là công cụ quan trọng giúp giảm thiểu các Higher-order Bugs.
Một số hoạt động kiểm thử có hiệu quả cao bao gồm:
Integration Testing.
System Testing.
Regression Testing.
Stress Testing.
Load Testing.
End-to-End Testing.
Việc kết hợp nhiều phương pháp kiểm thử khác nhau sẽ giúp tăng khả năng phát hiện các lỗi phức tạp này.
CHƯƠNG 3: NGUYÊN NHÂN HÌNH THÀNH HIGHER-ORDER BUGS
3.1 Giới thiệu
Higher-order Bugs là một trong những loại lỗi phức tạp và khó phát hiện nhất trong quá trình phát triển phần mềm. Không giống như các lỗi thông thường chỉ xuất hiện trong một chức năng riêng lẻ, Higher-order Bugs thường phát sinh từ sự tương tác giữa nhiều thành phần khác nhau của hệ thống. Chính vì vậy, việc hiểu rõ nguyên nhân hình thành loại lỗi này có ý nghĩa quan trọng trong việc xây dựng các chiến lược kiểm thử phù hợp.
Trong các hệ thống phần mềm hiện đại, số lượng module, dịch vụ và thành phần ngày càng tăng. Các thành phần này thường xuyên trao đổi dữ liệu với nhau và cùng tham gia xử lý một nghiệp vụ chung. Chỉ cần một sai lệch nhỏ trong quá trình tương tác cũng có thể dẫn đến những lỗi nghiêm trọng.
3.2 Sự tương tác giữa các module
Một trong những nguyên nhân phổ biến nhất dẫn đến Higher-order Bugs là sự tương tác giữa các module trong hệ thống.
Trong quá trình phát triển phần mềm, mỗi module thường được xây dựng bởi những nhóm phát triển khác nhau. Khi thực hiện kiểm thử đơn vị, từng module có thể hoạt động chính xác. Tuy nhiên, khi kết nối lại với nhau, sự khác biệt trong cách xử lý dữ liệu hoặc giao tiếp có thể tạo ra lỗi.
Ví dụ:
Module quản lý khách hàng lưu ngày sinh theo định dạng DD/MM/YYYY trong khi module báo cáo lại xử lý theo định dạng MM/DD/YYYY. Kết quả là dữ liệu bị hiển thị sai trong báo cáo.
Tình huống này cho thấy mặc dù từng module hoạt động đúng nhưng việc tích hợp giữa các module lại phát sinh lỗi.
3.3 Sai sót trong thiết kế hệ thống
Thiết kế hệ thống đóng vai trò quan trọng trong việc đảm bảo tính ổn định của phần mềm. Nếu kiến trúc hệ thống không được xây dựng hợp lý thì nguy cơ xuất hiện Higher-order Bugs sẽ tăng lên đáng kể.
Một số sai sót thường gặp trong giai đoạn thiết kế gồm:
Thiết kế luồng dữ liệu không rõ ràng.
Thiết kế giao diện giữa các module thiếu chặt chẽ.
Không xác định đầy đủ các trường hợp ngoại lệ.
Thiếu cơ chế xử lý lỗi khi các thành phần tương tác.
Những sai sót này có thể không gây ảnh hưởng ngay trong giai đoạn đầu nhưng sẽ trở thành nguyên nhân của nhiều lỗi phức tạp khi hệ thống mở rộng.
3.4 Dữ liệu không nhất quán
Dữ liệu là thành phần quan trọng trong mọi hệ thống phần mềm. Khi dữ liệu được truyền giữa nhiều module khác nhau, nếu không có cơ chế kiểm soát phù hợp thì rất dễ xảy ra tình trạng không nhất quán.
Một số nguyên nhân gây mất tính nhất quán dữ liệu:
Sử dụng nhiều nguồn dữ liệu khác nhau.
Thiếu cơ chế đồng bộ dữ liệu.
Xử lý dữ liệu theo các chuẩn khác nhau.
Sai lệch trong quá trình chuyển đổi dữ liệu.
Ví dụ:
Một hệ thống thương mại điện tử có module quản lý đơn hàng và module quản lý kho. Khi khách hàng đặt hàng thành công, module đơn hàng ghi nhận giao dịch nhưng module kho không cập nhật số lượng tồn kho. Điều này làm cho dữ liệu giữa hai hệ thống không đồng nhất.
3.5 Lỗi xử lý đồng thời (Concurrency Issues)
Trong các hệ thống hiện đại, nhiều người dùng có thể truy cập và sử dụng hệ thống cùng một lúc. Khi nhiều tiến trình đồng thời truy cập vào cùng một tài nguyên, nguy cơ xuất hiện lỗi sẽ tăng lên đáng kể.
Một số lỗi xử lý đồng thời phổ biến:
Race Condition
Race Condition xảy ra khi nhiều tiến trình cùng thay đổi dữ liệu tại một thời điểm.
Ví dụ:
Hai người dùng cùng thực hiện giao dịch chuyển tiền trên một tài khoản ngân hàng. Nếu hệ thống không kiểm soát đúng thứ tự xử lý thì số dư cuối cùng có thể bị tính sai.
Deadlock
Deadlock xảy ra khi hai hoặc nhiều tiến trình chờ tài nguyên của nhau và không thể tiếp tục thực hiện.
Data Corruption
Dữ liệu bị hỏng hoặc sai lệch do nhiều tiến trình ghi dữ liệu đồng thời.
Những lỗi này thường rất khó phát hiện vì chúng chỉ xuất hiện trong các điều kiện tải lớn hoặc trong các môi trường thực tế.
3.6 Thay đổi phần mềm trong quá trình phát triển
Trong thực tế, yêu cầu của khách hàng thường xuyên thay đổi. Việc bổ sung chức năng mới hoặc sửa đổi chức năng cũ có thể vô tình tạo ra Higher-order Bugs.
Ví dụ: Một chức năng mới được thêm vào hệ thống quản lý người dùng. Chức năng này hoạt động chính xác nhưng lại làm ảnh hưởng đến cơ chế phân quyền đã tồn tại trước đó.
Nếu không thực hiện kiểm thử hồi quy đầy đủ, những lỗi dạng này rất dễ bị bỏ sót.
3.7 Tích hợp với hệ thống bên ngoài
Nhiều phần mềm hiện nay không hoạt động độc lập mà phải tích hợp với các hệ thống khác như:
Cổng thanh toán.
Dịch vụ email.
API của bên thứ ba
Hệ thống quản lý dữ liệu.
Dịch vụ điện toán đám mây.
Mỗi hệ thống bên ngoài đều có cơ chế hoạt động riêng. Khi có sự thay đổi từ phía nhà cung cấp hoặc lỗi trong quá trình giao tiếp, hệ thống chính có thể phát sinh Higher-order Bugs.
Ví dụ:
Một website bán hàng tích hợp với cổng thanh toán trực tuyến. Khi nhà cung cấp thay đổi định dạng dữ liệu phản hồi nhưng hệ thống không được cập nhật tương ứng, quá trình thanh toán có thể gặp lỗi.
3.8 Thiếu kiểm thử tích hợp
Nhiều dự án tập trung vào kiểm thử đơn vị nhưng lại xem nhẹ kiểm thử tích hợp.
Điều này dẫn đến tình trạng:
Các module hoạt động đúng khi kiểm tra riêng lẻ.
Hệ thống phát sinh lỗi khi các module làm việc cùng nhau.
Kiểm thử tích hợp là một trong những phương pháp quan trọng nhất để phát hiện Higher-order Bugs. Nếu hoạt động này không được thực hiện đầy đủ thì nhiều lỗi sẽ chỉ xuất hiện sau khi triển khai thực tế.
3.9 Độ phức tạp của hệ thống
Khi quy mô hệ thống tăng lên, số lượng tương tác giữa các thành phần cũng tăng theo cấp số nhân.
Ví dụ:
Một hệ thống có 5 module sẽ có ít mối liên kết hơn nhiều so với hệ thống có 50 module.
Độ phức tạp càng cao thì khả năng xuất hiện Higher-order Bugs càng lớn. Đây là lý do các hệ thống doanh nghiệp lớn thường phải đầu tư nhiều nguồn lực cho hoạt động kiểm thử.
3.10 Yếu tố con người
Con người luôn là một trong những nguyên nhân dẫn đến lỗi phần mềm.
Một số nguyên nhân phổ biến gồm:
Hiểu sai yêu cầu.
Lập trình không tuân thủ tiêu chuẩn.
Thiếu kinh nghiệm phát triển.
Thiếu giao tiếp giữa các nhóm dự án.
Thiếu tài liệu kỹ thuật.
Những sai sót này có thể tạo ra các lỗi tiềm ẩn và chỉ xuất hiện khi nhiều thành phần tương tác với nhau.
3.11 Kết luận chương
Higher-order Bugs có thể hình thành từ nhiều nguyên nhân khác nhau như sự tương tác giữa các module, lỗi thiết kế hệ thống, dữ liệu không nhất quán, xử lý đồng thời, thay đổi phần mềm, tích hợp với hệ thống bên ngoài và yếu tố con người. Việc nhận diện đầy đủ các nguyên nhân này giúp nhóm phát triển xây dựng chiến lược kiểm thử phù hợp nhằm giảm thiểu rủi ro và nâng cao chất lượng sản phẩm phần mềm.












CHƯƠNG 4: PHƯƠNG PHÁP PHÁT HIỆN VÀ XỬ LÝ HIGHER-ORDER BUGS
4.1 Kiểm thử tích hợp (Integration Testing)
Kiểm thử tích hợp là phương pháp quan trọng nhất để phát hiện Higher-order Bugs, vì loại lỗi này chủ yếu xuất hiện khi các module tương tác với nhau.
Mục tiêu của kiểm thử tích hợp là kiểm tra sự hoạt động đúng đắn của các module khi được kết nối lại thành một hệ thống hoàn chỉnh.
Trong thực tế, từng module có thể hoạt động đúng khi kiểm thử đơn lẻ, nhưng khi ghép lại có thể xảy ra lỗi như sai dữ liệu, sai luồng xử lý hoặc lỗi giao tiếp giữa các thành phần.
Ví dụ: module thanh toán xử lý đúng, module đặt hàng xử lý đúng, nhưng khi kết hợp lại thì đơn hàng không được cập nhật trạng thái.
4.2 Các chiến lược kiểm thử tích hợp
Top-down testing
Kiểm thử từ module cấp cao xuống thấp. Ưu điểm là thấy được luồng nghiệp vụ sớm, nhưng cần stub để giả lập module chưa hoàn thành.
Bottom-up testing
Kiểm thử từ module thấp lên cao. Dễ kiểm soát từng thành phần nhưng khó đánh giá toàn hệ thống sớm.
Hybrid testing
Kết hợp cả hai phương pháp trên, giúp cân bằng giữa kiểm soát và đánh giá hệ thống.
4.3 Kiểm thử hệ thống (System Testing)
Kiểm thử hệ thống được thực hiện trên toàn bộ ứng dụng đã tích hợp hoàn chỉnh. Mục tiêu là kiểm tra hệ thống hoạt động đúng theo yêu cầu nghiệp vụ.
Loại kiểm thử này giúp phát hiện các lỗi liên quan đến nhiều thành phần như:
Lỗi luồng nghiệp vụ 
Lỗi dữ liệu 
Lỗi giao tiếp giữa các module 
4.4 Kiểm thử đầu cuối (End-to-End Testing)
End-to-End Testing mô phỏng hành vi người dùng thực tế từ đầu đến cuối quy trình.
Ví dụ:
Đăng nhập → chọn sản phẩm → đặt hàng → thanh toán → nhận xác nhận.
Nếu bất kỳ bước nào bị lỗi, toàn bộ quy trình sẽ bị ảnh hưởng.
4.5 Kiểm thử hồi quy (Regression Testing)
Regression Testing đảm bảo rằng các thay đổi mới không làm ảnh hưởng đến chức năng cũ của hệ thống.
Đây là bước rất quan trọng vì khi sửa một lỗi hoặc thêm tính năng mới, có thể vô tình tạo ra lỗi ở phần khác của hệ thống.
4.6 Kiểm thử hiệu năng (Performance Testing)
Kiểm thử hiệu năng giúp phát hiện lỗi khi hệ thống hoạt động dưới tải lớn.
Bao gồm:
Load Testing: kiểm tra tải bình thường 
Stress Testing: kiểm tra vượt tải 
Volume Testing: kiểm tra dữ liệu lớn 
Loại kiểm thử này giúp phát hiện các lỗi chỉ xuất hiện khi hệ thống có nhiều người dùng đồng thời.
4.7 Kiểm thử tự động (Automation Testing)
Kiểm thử tự động giúp tăng tốc độ kiểm thử và giảm sai sót do con người.
Ưu điểm:
Thực hiện nhanh 
Lặp lại nhiều lần 
Phù hợp kiểm thử hồi quy 
Công cụ phổ biến: Selenium, Cypress, Postman, JUnit.
4.8 Quy trình xử lý Higher-order Bugs
Khi phát hiện lỗi, quy trình xử lý gồm:
1.Ghi nhận lỗi (bug report) 
2.Tái hiện lỗi 
3.Phân tích nguyên nhân 
4.Xác định module gây lỗi 
5.Sửa lỗi 
6.Kiểm thử lại 
7.Kiểm thử hồi quy 
4.9 Kết luận chương
Việc kết hợp nhiều phương pháp kiểm thử như integration testing, system testing và regression testing giúp tăng khả năng phát hiện Higher-order Bugs và đảm bảo chất lượng phần mềm.











CHƯƠNG 5: GIỚI HẠN CỦA KIỂM THỬ PHẦN MỀM
5.1 Kiểm thử không thể chứng minh phần mềm đúng hoàn toàn
Một hiểu lầm phổ biến trong phát triển phần mềm là cho rằng nếu hệ thống đã qua nhiều bước kiểm thử và không phát hiện lỗi thì hệ thống đó “đúng hoàn toàn”. Tuy nhiên, trong thực tế, kiểm thử chỉ có thể chứng minh sự tồn tại của lỗi, chứ không thể chứng minh sự vắng mặt của lỗi.
Điều này xuất phát từ bản chất của kiểm thử: tester chỉ có thể chạy một số hữu hạn trường hợp trong khi không gian đầu vào của phần mềm là vô hạn. Vì vậy, luôn tồn tại khả năng có những tình huống chưa được kiểm thử.
Ví dụ, một hệ thống thương mại điện tử có thể hoạt động ổn định với 1.000 test case, nhưng vẫn có thể phát sinh lỗi khi gặp hàng triệu người dùng truy cập đồng thời.
5.2 Không thể kiểm thử toàn bộ trường hợp
Trong thực tế, số lượng trường hợp kiểm thử tăng theo cấp số nhân khi số lượng input tăng lên. Ngay cả một chức năng đơn giản như đăng nhập cũng có thể tạo ra hàng triệu tổ hợp dữ liệu khác nhau nếu tính đến:
Username 
Password 
OTP 
Trạng thái tài khoản 
Loại thiết bị 
Do đó, việc kiểm thử toàn bộ là không khả thi về mặt lý thuyết lẫn thực tiễn. Tester phải lựa chọn các trường hợp có xác suất xảy ra lỗi cao nhất dựa trên kinh nghiệm và phân tích rủi ro.
5.3 Giới hạn về thời gian và chi phí
Trong mọi dự án phần mềm, thời gian và ngân sách luôn bị giới hạn. Điều này ảnh hưởng trực tiếp đến hoạt động kiểm thử.
Khi thời gian gấp rút, nhóm kiểm thử buộc phải giảm số lượng test case hoặc rút ngắn quy trình kiểm thử. Điều này làm tăng nguy cơ bỏ sót các lỗi phức tạp, đặc biệt là Higher-order Bugs – vốn chỉ xuất hiện trong các tình huống kết hợp phức tạp.
Tương tự, ngân sách hạn chế cũng làm giảm khả năng sử dụng công cụ kiểm thử hiện đại hoặc xây dựng môi trường kiểm thử đầy đủ như thực tế.
5.4 Giới hạn về dữ liệu kiểm thử
Dữ liệu kiểm thử thường được tạo giả lập, không phản ánh hoàn toàn dữ liệu thực tế. Trong khi đó, dữ liệu thực tế có thể rất phức tạp, bao gồm dữ liệu lớn, dữ liệu lỗi, hoặc dữ liệu không hợp lệ.
Điều này dẫn đến việc một số lỗi chỉ xuất hiện khi hệ thống hoạt động thật, đặc biệt là các lỗi liên quan đến xử lý dữ liệu lớn hoặc dữ liệu bất thường.
5.5 Giới hạn về môi trường kiểm thử
Môi trường kiểm thử thường không giống môi trường production. Ví dụ:
Test: ít người dùng, ít server 
Production: nhiều người dùng, hệ thống phân tán 
Sự khác biệt này khiến một số lỗi chỉ xuất hiện khi hệ thống hoạt động thực tế, chẳng hạn như lỗi hiệu năng, lỗi đồng bộ dữ liệu hoặc lỗi xử lý đồng thời.
5.6 Giới hạn của kiểm thử tự động
Kiểm thử tự động giúp tăng tốc độ và giảm sai sót, nhưng không thể thay thế hoàn toàn kiểm thử thủ công.
Một số hạn chế của kiểm thử tự động gồm:
Không đánh giá được trải nghiệm người dùng 
Khó phát hiện lỗi logic phức tạp 
Chi phí bảo trì test script cao 
Do đó, kiểm thử tự động chỉ nên được xem là công cụ hỗ trợ, không phải giải pháp thay thế hoàn toàn.
5.7 Hiện tượng Pesticide Paradox
Pesticide Paradox là hiện tượng khi một bộ test case được sử dụng lâu dài sẽ dần mất hiệu quả. Nguyên nhân là vì hệ thống phần mềm luôn thay đổi, trong khi test case không được cập nhật tương ứng.
Điều này dẫn đến việc các lỗi mới không còn được phát hiện. Vì vậy, bộ test cần được thường xuyên cập nhật, mở rộng và cải tiến.
5.8 Kết luận chương
Kiểm thử phần mềm tồn tại nhiều giới hạn cả về lý thuyết lẫn thực tế. Không thể kiểm thử toàn bộ hệ thống, không thể đảm bảo phát hiện hết lỗi, và cũng không thể loại bỏ hoàn toàn rủi ro.
Do đó, mục tiêu thực tế của kiểm thử là giảm thiểu lỗi đến mức thấp nhất có thể, thay vì cố gắng đạt trạng thái “không còn lỗi”.


































CHƯƠNG 6: GIẢI PHÁP NÂNG CAO HIỆU QUẢ KIỂM THỬ VÀ GIẢM THIỂU HIGHER-ORDER BUGS
6.1 Cải thiện thiết kế hệ thống
Một trong những cách hiệu quả nhất để giảm Higher-order Bugs là cải thiện thiết kế hệ thống ngay từ đầu. Khi kiến trúc phần mềm rõ ràng, các module được tách biệt hợp lý và có giao tiếp chuẩn hóa, khả năng phát sinh lỗi do tương tác sẽ giảm đáng kể.
Các nguyên tắc cần áp dụng gồm:
Giảm phụ thuộc giữa các module 
Thiết kế theo hướng module hóa 
Chuẩn hóa API và luồng dữ liệu 
Tách biệt rõ logic nghiệp vụ và xử lý dữ liệu 
6.2 Tăng cường kiểm thử tích hợp
Integration Testing là tuyến phòng thủ quan trọng nhất đối với Higher-order Bugs. Thay vì chỉ kiểm tra từng module riêng lẻ, cần tập trung vào cách các module làm việc cùng nhau.
Cần chú ý:
Kiểm tra luồng dữ liệu giữa các module 
Kiểm tra tương thích dữ liệu 
Kiểm tra các trường hợp lỗi khi tích hợp 
Kiểm tra các tình huống bất thường 
6.3 Kiểm thử hồi quy (Regression Testing)
Mỗi khi hệ thống thay đổi, luôn có nguy cơ phát sinh lỗi mới. Regression testing đảm bảo rằng các chức năng cũ vẫn hoạt động đúng sau khi cập nhật.
Đây là bước quan trọng để tránh lỗi dây chuyền trong hệ thống lớn.
6.4 Kiểm thử hiệu năng
Higher-order Bugs thường xuất hiện khi hệ thống chịu tải lớn hoặc hoạt động lâu dài.
Do đó cần thực hiện:
Load testing để kiểm tra tải bình thường 
Stress testing để kiểm tra giới hạn hệ thống 
Volume testing để kiểm tra dữ liệu lớn 
6.5 Kiểm thử tự động
Kiểm thử tự động giúp tăng tốc độ kiểm thử và đảm bảo tính lặp lại của test case.
Lợi ích:
Giảm thời gian kiểm thử 
Tăng độ chính xác 
Hỗ trợ regression testing hiệu quả 
6.6 DevOps và CI/CD
Việc tích hợp kiểm thử vào quy trình CI/CD giúp phát hiện lỗi sớm ngay từ khi code được đưa lên hệ thống. Điều này giúp giảm đáng kể chi phí sửa lỗi ở giai đoạn cuối.
6.7 Giám sát hệ thống sau triển khai
Không phải tất cả lỗi đều có thể phát hiện trước khi release. Vì vậy cần có hệ thống giám sát sau triển khai để:
Theo dõi hiệu năng hệ thống 
Phát hiện lỗi thực tế 
Ghi log và phân tích sự cố 
Thu thập phản hồi người dùng 
6.8 Đào tạo nhân sự kiểm thử
Con người vẫn là yếu tố quyết định chất lượng kiểm thử. Một tester giỏi cần:
Hiểu nghiệp vụ 
Hiểu kiến trúc hệ thống 
Có kỹ năng phân tích lỗi 
Biết thiết kế test case hiệu quả 


KẾT LUẬN
Trong quá trình phát triển phần mềm, kiểm thử đóng vai trò quan trọng trong việc đảm bảo chất lượng sản phẩm và giảm thiểu các rủi ro khi triển khai thực tế. Tuy nhiên, kiểm thử không phải là hoạt động có thể đảm bảo phát hiện toàn bộ lỗi tồn tại trong hệ thống.
Thông qua việc nghiên cứu đề tài “Higher-order Bugs và Giới hạn của kiểm thử”, có thể thấy rằng Higher-order Bugs là một trong những nhóm lỗi phức tạp và khó phát hiện nhất. Các lỗi này thường xuất hiện do sự tương tác giữa nhiều thành phần, nhiều module hoặc nhiều dịch vụ khác nhau trong hệ thống. Mặc dù từng thành phần có thể hoạt động chính xác khi kiểm thử riêng lẻ, nhưng khi kết hợp với nhau vẫn có khả năng phát sinh lỗi.
Báo cáo đã phân tích các nguyên nhân hình thành Higher-order Bugs như lỗi tích hợp, dữ liệu không nhất quán, xử lý đồng thời, thay đổi phần mềm và sự phức tạp của hệ thống. Đồng thời, các phương pháp phát hiện và xử lý lỗi cũng được trình bày nhằm giúp nâng cao hiệu quả kiểm thử.
Bên cạnh đó, đề tài cũng làm rõ các giới hạn của kiểm thử phần mềm bao gồm giới hạn về thời gian, chi phí, dữ liệu, môi trường kiểm thử và nguồn nhân lực. Những giới hạn này cho thấy kiểm thử chỉ có thể làm giảm rủi ro chứ không thể loại bỏ hoàn toàn lỗi trong phần mềm.
Từ những nội dung đã nghiên cứu, có thể khẳng định rằng việc kết hợp nhiều phương pháp kiểm thử khác nhau cùng với quy trình phát triển phần mềm khoa học là giải pháp hiệu quả nhằm nâng cao chất lượng sản phẩm và giảm thiểu nguy cơ phát sinh Higher-order Bugs trong thực tế.





TÀI LIỆU THAM KHẢO
[1] Glenford J. Myers, The Art of Software Testing, John Wiley & Sons.
[2] Roger S. Pressman, Software Engineering: A Practitioner's Approach.
[3] Ian Sommerville, Software Engineering.
[4] Paul Ammann & Jeff Offutt, Introduction to Software Testing.
[5] Boris Beizer, Software Testing Techniques.
[6] Cem Kaner, Jack Falk & Hung Quoc Nguyen, Testing Computer Software.
[7] ISO/IEC 25010: Systems and Software Quality Requirements and Evaluation.
[8] ISTQB Foundation Level Syllabus.
[9] Giáo trình Đảm bảo chất lượng phần mềm, các trường Đại học Công nghệ Thông tin.
[10] Giáo trình Kiểm thử phần mềm, Bộ môn Công nghệ phần mềm.
[11] IEEE Standard for Software Test Documentation.
[12] Tài liệu học phần Đảm bảo chất lượng và Kiểm thử phần mềm.












