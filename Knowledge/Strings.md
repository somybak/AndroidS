String a = "231131";
		String b = "12345";
		String c = "231131";
		
		//1.���ڿ� ��
		// ���ڿ�.compareTo(���ڿ�)
		// ���ڿ�.equals(���ڿ�) ���ϱ�
		// ���ڿ� == ���ڿ�
		
		System.out.println(a.compareTo(b));
		System.out.println(a.compareTo(c));
		if(a.equals(c)){
			System.out.println("a�� b�� �����ϴ�.");
		}
		
		System.out.println(a.equals(b));
		System.out.println(a.equals(c)); // �ΰ� ���ڿ��� ������ true
		
		//2. ���ڿ��� �ε��� ��
		// � ������ ��ġ�� ������. ���� ���̻��̸��� ���ڰ� ����. ������ ������ ���� ����.
		// subString�� ���
				
		System.out.println(a.charAt(2));
		
		// 3. ���ڿ� ������ '+' ���
		System.out.println(a + b);
		
		// 4. "����" ���� �����ϴ� ���ڿ�����.. "����"���� ��������
		System.out.println(a.startsWith("23"));
		System.out.println(a.endsWith("23"));
		
		// 5. ã�����ϴ� ���ڿ��� ���° �ִ���... String �Լ� �߿�
		// �� ó���� ������ �� �ϳ��� ������
		// Last �� ���̸� �ڿ������� ã��
		// ã�� ���ڿ��� ������ -1 ����
		System.out.println(a.indexOf("3"));
		
		// 6. ���ڿ� ����
		System.out.println(a.length());
		
		// 7. ���ڿ� ����
		// �Ѱ��� �ٲ�... replaceAll ("���ڿ��� ���� : ���Խ�","�ٲ� ����")
		//���ڷ� �����ϴ� � ���ڴ� ���� ���ϴ� ���ڷ� �ٲ���
		System.out.println(a.replace("1","X"));
		
		//uppercase - �빮�� �ҹ��� �ٲ���
		//8. ���ڿ� �ڸ��� (����)���� �ڸ�. (a,b) a�� b ������ ���ڸ� ������
		System.out.println(a.substring(3));
		System.out.println(a.substring(3,4));
		
		//9.���ڿ� �и��ϱ� split. �迭�� ����� (��ȣ)�� ���ڸ� �������� �� ©�� ����.
		String value = "a/b/cdg/a2223/afefs";
		String values[] = value.split("/");
		for(String item : values) {
			System.out.println(item);
		}		
				
		// 10. ���� -> ���ں�ȯ = ����""
		String ccc = 888+"";
		
		// 11. ���� -> ���ں�ȯ
		int ddd = Integer.parseInt(ccc);
		long eee = Long.parseLong(ccc);
		
		//12. int -> char ��ȯ = char �������� ū ���� �ԷµǸ� �����
		char fff = (char)ddd;
		
		// 13. �ϳ��� ���ڸ� char�� ���� = ����: ���ڿ����� ȿ����
		        int argNum   =  8; // �Է��ϴ� ����
		        int argDigix = 10; // ����
		        char cha = Character.forDigit(argNum, argDigix);
		// 14. ���ڿ��� �ѱ��ھ� char�� �����ؼ� �迭�� ����
		        String target = "8888";
		        char arrs[] = target.toCharArray();
		        
		//15. �迭 ����
		       Arrays.sort(arrs);
		        //arrs = ���� �̹� �Ǽ� ���ķ� arrs ���� �� ���ĵǾ� ����
		        

	}