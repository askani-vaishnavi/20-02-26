class Solution(object):
    def makeLargestSpecial(self, s):
        count = 0
        start = 0
        parts = []

        for i, ch in enumerate(s):
            if ch == '1':
                count += 1
            else:
                count -= 1

            # Found a special substring
            if count == 0:
                # Process inner substring recursively
                inner = self.makeLargestSpecial(s[start + 1:i])
                parts.append('1' + inner + '0')
                start = i + 1

        # Sort in descending order to make largest
        parts.sort(reverse=True)

        return ''.join(parts)# 20-02-26
